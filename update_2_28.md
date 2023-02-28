
### Completed
- Design
- Backend & Authentication
- App Builder Component Modifications (Partial)

### In Progress
- Customizations API Modifications

---

### App Structure

The idea here is to create a custom react app that handles every part of the application up to creating and joining a room. The only part the app builder component would handle would be the `precall` & `call` screen

`<App/>`
 - `/home`
 - `/profile/:username`
 - `/create-room`
 - `/join-room/:room_id`
 - `/room/:room_id`
    - `<AppBuilderReactSDK.View />`
        - PreCall Screen
        - Call Screen


---

### Work Flow With Customizations API

<br/>


**Custom Create Room Form: In Progress**

Looking for best approach to for implementing `useCeateMeeting` outside of App Builder component.

Current Issue: Hook is not available outside of app builder component, my belief is that it should be.

Note: May have to look into calling backend directly with Apollo client

```tsx
import { useCreateMeeting } from "@appbuilder/react";

const CreateRoomForm = () => {
    const createMeeting = useCreateMeeting()

    const [roomDetails, setRoomDetails] = useState({
                name:'',
                description:'',
                thumbnail:null,
                date:null
        })

    const handleFormSubmit = async (e) => {
        let {host_id, attendee_id} = await createMeeting(roomDetails.name)
        
        //Send room details to backend to be saved and scheduled
        await addRoomToDB(roomDetails)
    }
    ...
}
```

**On `join` Event Listener: In Progress**

In order to display custom user information beyond just a user name, I am attempting to send a custom event to the room when a new user joins so all other users can receive the new users info and update their local state. 

At this point the `join` event is not working correctly: It seems to be calling the send method before a client is actually logged in.

Here is the ideal implementation:

```tsx
AppBuilderReactSDK.on('join', () => {

    customEvents.send('custom_info', JSON.stringify({avatar, handle, ...}), 2)

    customEvents.on('custom_info', (data) => {
        //Update the local `users` state with `data`.
        users[sender_uid] = data
    })
})
```

---

<br/>

### Progess We Have Made So Far

**"appRoot" & "useUserContext" Added**

These two additions provide a way to wrap the app builder `View` component and pass state down, making it easer to add my own custom state for authentication and additional data like custom user infomation.

```tsx
export const AppRootProvider = ({children}) => {
  
  const [avatar, setAvatar] = useState(...)
  const [username, setUserName] = useState(...)

  const [participants, setParticipants] = useState([])

      AppBuilderReactSDK.customize({
        components:{
            appRoot:AppRootProvider,
            ...
        })


const HeaderBar () => {
    const {avatar, username} = useContext(AppRootContext)

    return <nav>
                <p>Hello, {username}</p>
                <img src={avatar}/>
            </nav>
}
```
