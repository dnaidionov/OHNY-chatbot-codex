# Privacy Notice

## Implements Requirements
- REQ-CHECKIN-007
- REQ-PRIV-001
- REQ-PRIV-002
- REQ-PRIV-003
- REQ-PRIV-004
- REQ-PRIV-005
- REQ-PRIV-006
- REQ-PRIV-008
- REQ-PRIV-009
- REQ-PRIV-010
- REQ-OPS-002

## Purpose
Explain in user-facing language what information the OHNY chatbot may store on the device, what it may send to the server, and how users can clear saved data.

## What Stays On Your Device
- The chatbot may save your check-in information on this device only if you explicitly say yes.
- The chatbot may also save planning preferences on this device, such as your interests, accessibility preferences, and lightweight convenience settings.
- Saved device data is meant to make repeat planning and repeat check-ins faster.
- We should not save highly sensitive free-form notes or other data that is not useful for future check-ins.

## What We Send To The Server
- When you ask to check in, the chatbot sends the information required to complete that check-in through a thin backend proxy to the existing OHNY check-in system.
- This may include the resolved site and the required check-in fields you confirm before submission.
- If you allow location access and your check-in flow uses it to identify a site, the system may send only the location-derived result or the minimum location-related information needed for that check-in flow.
- The chatbot does not create a server-side personal profile for you in v1.

## Geolocation
- The app asks for location access to improve `near me` recommendations and unnamed check-ins.
- Location access is optional.
- If you deny location access, the chatbot should still work and will ask for a site name, neighborhood, landmark, or address fragment instead.
- If location access is requested again later, the app should explain why it would help with the current task.

## Consent
- The chatbot must ask before saving check-in information on this device.
- The save prompt must clearly say that the information is stored on this device only, not in a server-side profile.
- Your save choice should remain in effect until you revoke it or the saved data materially changes.
- At the start of a new OHNY season, the app may ask whether previously saved check-in info is still valid before reusing it.

## Forgetting Saved Data
- You can ask the chatbot to `forget my info` to clear saved local check-in/profile data on this device.
- This action should also be available in settings or options.
- Planning preferences should be managed separately, so the app should also offer a separate way to reset saved planning preferences.

## Analytics And Monitoring
- v1 should use aggregate operational analytics only.
- v1 should not keep server-side personal profiles or raw chat-linked PII just for analytics.
- Monitoring may track service health, latency, and failure rates in aggregate so the product can remain reliable during OHNY weekend.

## Outside OHNY Weekend
- If you try to check in outside OHNY weekend, the app should warn you that the check-in system may be unavailable.
- If the attempt fails, the app should explain that the OHNY check-in service may be down because the event window is not active.
