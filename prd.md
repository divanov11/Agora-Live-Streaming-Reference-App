# Interactive Live Streaming Reference App

Truly interactive live streaming for gaming, live events and more. 

1. Stream Events 
2. Message & Voice chat with Audiance
3. Broadcast streams on youtube
4. Record Events

## Summary

Think Twitch, Club House and Streamyards, all in one application. This is a place where users can schedule and host events with a live audience via chat, along with the ability to bring up audience memebers to speak via voice chat, just like you would on a twitter spaces or club house call. 

Streams can also be recorded and or boradcasted to 3rd party platforms like youtube. 


<img src="images/pages_preview.png" />


## Purpose & Target Audiance

This reference app targets the **`social`** and **`gaming`** vertical and provides a starting point for anyone looking for to add interactive live streaming features. This application will give a foundation for anyone looking to build something simular or features from the following virtual events organizations:

- `Twitch` - Interactive Live Streaming
- `Twitter` spaces/clubhouse - Voice chat
- `Stream Yards` - 3rd party broadcasting


## Tech Stack
- Backend: Django (Python)
- Frontend: React
- Database: Postgres (SQLite for demo)
- Hosting: Railway (Backend)/ Vercel (Frontend)
- Agora RTM, RTC

## Structure Diagram

<img src="images/diagram.png"/>


## Functional Requirements

| Requirement | Description |
| ------- | ------------------------------ |
 Video Stream |  <ul><li>Join & Leave Call</li><li>Toggle Mic & Video (on/off)</li><li>Screen Share</li></ul>
Voice Call |  <ul><li>Join & Leave Call</li><li>Display user name & avatar</li><li>Toggle Mic & Video (on/off)</li><li>Admin controls over guests</li></ul>
Live Chat |  <ul><li>Send & Recieve Messages</li></ul>
Cloud Recording |  <ul><li>Record Streams</li><li>Store Streams</li><li>Access Previous Streams</li></ul>
Broadcast to youtube |  <ul><li>Push Stream to 3rd party platforms</li></ul>


## Feature Specification

1. **Video Stream**
   1. Feature - Join & Leave Call
      1. Details - Join channel, publish & unpuiblish streams
      2. Agora Tools - RTC & Token Server
   2. Feature - Toggle Mic & Video
      1. Details - Host can mute mic & camera. H
      2. Agora Tools - RTC
   3. Feature: Screen Share
      1. Details: Host can share screen(s) & toggle bewtween video & screen at any point
      2. Agora Tools: RTC

2. **Voice Call**
   1. Feature - Join & Leave Call
      1. Details - Join channel, publish & unpuiblish streams (voice)
      2. Agora Tools - RTC & RTM
   2. Feature - Toggle Mic
      1. Details - Host & Participants can mute mic. Host can toglge guests controls.
      2. Agora Tools - RTC & RTM
   3. Feature: Display user name & avatar
      1. Details: Usernames & avatar display on remote guest screens
      2. Agora Tools: RTM
   4. Admin controls over guests
      1. Details: Host has full control over guests mic & can invite or kick guests when they need.
      2. Agora Tools: RTM
3. **Live Chat**
   1. Feature: Send & Recieve Messages
      1. Details: Real time chat during stream with host and guests
      2. Agora Tools: RTM
4. **Cloud Recording**
   1. Feature: Record Streams
      1. Details: Toggle stream recoring at any time
      2. Agora Tools: Cloud Recording, RTC, RESTful API
   2. Feature: Store streams 
      1. Details: Streams will be uploaded into an AWS S3 Bucket
      2. Agora Tools: RESTful API
   3. Feature: Access Previous Streams
      1. Details: Pulling streams form S3 Bucket for later viewership
      2. Agora Tools:: N/A
5. **Broadcast to youtube**
   1. Feature: Push Streams Live to youtube
      1. Details: Streams can be boradcasted on multiple platforms, live.
      2. Agoora Tools: Media Push, RTC
      
      
### Timeline/Steps

| Description | Estimate |
|-------------|----------|
App Builder Code & API Breakdown | 5d |
UI Customization/Modifications | 7d |
Custom Backend With Auth | 3d |
Cloud Recording | 2d |
3rd Party RTMP Push   | 5d |
