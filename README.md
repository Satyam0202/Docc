# memory_vault

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Learn Flutter](https://docs.flutter.dev/get-started/learn-flutter)
- [Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Flutter learning resources](https://docs.flutter.dev/reference/learning-resources)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.

## Laptop local file sharing

1. Connect the phone and laptop to the same Wi-Fi, or connect the laptop to the
   phone's hotspot.
2. In Keepsake, open **Profile → Laptop & phone file sharing → Start sharing**.
   Note the phone URL and temporary six-digit PIN. A persistent notification
   keeps sharing available while you use other apps or lock the screen. Android
   force-stop, battery restrictions, or stopping sharing will end the server.
3. On Windows, open PowerShell in this project folder and run:

   ```powershell
   python -m http.server 8766 --directory tools
   ```

4. Open `http://localhost:8766/local_share_laptop.html` in the laptop browser.
   Enter the phone URL shown in Keepsake, press **Connect**, then enter the PIN.
5. Upload laptop files, download shared phone files, or chat. The PIN is still
   required to pair; it protects files from other devices on the network. Stop
   sharing in Keepsake when finished. Keep the laptop page server and phone
   sharing limited to a trusted local network; the phone connection uses HTTP,
   not encryption.

## Mirror phone notifications to the desktop pet

Run **My AI Desktop Pet** from `D:\pet` and connect the phone and laptop to the
same trusted Wi-Fi network or phone hotspot. Find the laptop's Wi-Fi IPv4
address with `ipconfig`. In Keepsake, open
**Profile → Desktop pet notifications**, enter the laptop's private IPv4
address, and connect. Select **Open notification access settings** and
explicitly enable Keepsake. New notifications bring PET forward and show a
small dot on it; click the dot to open the recent session inbox. Disconnect in
Keepsake to stop mirroring.
When an app's phone-call notification exposes **Answer**, **Decline**, or **End**
actions, PET shows those controls on that notification. Enter the phone control
code in PET to send an action; notification actions expire and may stop working
when the phone or calling app dismisses them. Apps that do not expose call
actions cannot be remotely controlled this way. Call audio stays on the phone;
Android does not let Keepsake relay ordinary cellular or third-party app call
audio to PET.

To place calls or send SMS directly from PET, enable **Direct calls and SMS**
on this screen and grant both Android permissions once. Copy the six-digit
phone control code shown here, then in PET right-click the companion and choose
**Call or text from phone**. Enter the code and recipient number; **Call now**
or **Send SMS** sends directly without opening a composer or asking for
per-action confirmation. Calls/SMS still require working phone service and may
incur carrier charges. Keep the control code private and use the feature only
on a trusted local network.
The phone panel also has **End call**. Grant the call-control permission in
Keepsake when prompted; ending calls requires Android 9 or later.

To view SMS stored on the phone, choose **Enable SMS history in PET** on the
same screen and grant Android's SMS permission. Connect Keepsake to PET, then
type `message_history` in PET or choose **Message history** from its menu.
Enter the six-digit phone control code if prompted. PET shows sent and received
SMS; use **Hide** on one message or **Clear history from PET** to clear the
current PET view only. These options do not delete SMS from the phone; loading
history again can show them again. Android does not expose WhatsApp or other
apps' private chats this way.
SMS contents are sensitive and the local relay is unencrypted, so use this
feature only on a trusted Wi-Fi network or hotspot.

For WhatsApp, SMS, and other messaging notifications that expose Android's
inline **Reply** action, PET shows a reply field in the notification card.
Replies use the app's active notification action and can fail if it expires;
apps without an inline text-reply action cannot be replied to from PET. This
does not give PET access to private WhatsApp chats or message history. When a
notification includes an image attachment, Keepsake sends PET a small,
compressed preview; the original photo is not copied. Some apps do not include
the image in the notification, so those photos cannot be previewed there.
Notification text and thumbnails travel over the unencrypted local relay, so
use it only on a trusted network.
Automatic pet movement pauses while a phone panel is open; drag the pet to
move it manually.

To start a call or text flow, double-click the pet, type `phone` (or `call` /
`sms`), then enter the control code and phone number in its panel. Enter a
message and choose **Send SMS**, or choose **Call now**. The word typed in the
chat only opens the panel; it does not place a call or send an SMS by itself.
Choose **End call** to end an active phone call.

## Stream phone camera and microphone to PET

Connect Keepsake and PET on the same trusted Wi-Fi network or phone hotspot.
In Keepsake's **Desktop pet notifications** screen, select **Start PET stream**
and grant camera and microphone access. The phone shows an ongoing Keepsake
notification while both sensors are active; streaming can continue while
Keepsake is minimized. Type `stream_phone` in PET to start the phone camera and
microphone and connect automatically. Enter the six-digit phone control code
once if PET asks for it. Android still requires camera and microphone
permissions to be granted on the phone; the system may show those prompts the
first time. Use **Switch front/back camera** and **Speaker on/off** in PET.
**Stop PET stream** in Keepsake or **Stop phone stream** in PET stops capture.
The existing **Start PET stream** button in Keepsake remains available.

Streaming is always user-started, is not recorded by Keepsake or PET, and should
only be used on a trusted local network. WebRTC sends media directly between
devices with encrypted media transport; the local signaling relay is not
encrypted. This direct local connection has no internet/TURN fallback and may
not work when Wi-Fi client isolation blocks devices from reaching each other.
Android's persistent notification remains visible while capture is active.

To share the **phone screen** instead, select **Start screen share** in
Keepsake's same screen and approve Android's screen-capture prompt. PET shows
the screen in its stream panel. Alternatively, type **`phone screen`** in PET
and enter the six-digit phone control code once in PET's chat. PET connects
automatically when the phone's stream offer arrives; the code stays in PET
memory until PET exits. Android still requires approval of its system
screen-capture prompt on the phone for each new sharing session; Android does
not let apps save or bypass that approval. Closing PET's viewer now hides it
without ending the active share, so reopen it with `phone screen` without
starting a new Android session. Use **Stop sharing** in PET or stop the share
on the phone to end the session; Android will ask again the next time a new
session starts. Android keeps its sharing notification. Choose **Full screen**
in PET to view the stream at
desktop size; press **Esc** to exit. Screen sharing currently sends video only;
movie/app playback audio is not included. **Save screenshot** downloads the
currently displayed frame to the laptop. Select an installed app in PET and choose
**Open app** to request that it open on the phone. Android blocks apps from
launching over other apps while Keepsake is in the background, so tap the
Keepsake notification on the phone to open the requested app. Screen sharing
stops from either app or when Android revokes screen-capture access. For apps
that permit playback capture, Android 10+ can also send playback audio to PET;
tap **Speaker on** in the viewer. Some apps, DRM video, and protected content
block playback capture, so audio is not guaranteed. Android may request its
microphone permission because playback capture requires `RECORD_AUDIO`; denying
it still allows video-only screen sharing. Playback audio is sent over the
encrypted WebRTC connection, not the local signaling relay.

Android requires this special access and may hide notification contents for
privacy. Only notification titles and preview text exposed by Android are sent.
Mirroring uses unencrypted local HTTP, so do not enable it on an untrusted
network. The pet keeps up to 50 received previews in memory until it exits.
Do not force-stop Keepsake; Android's battery controls may also affect background
delivery.

## Standalone Nearby Share app

The independent Android app is in [`tools/nearby_share_app`](tools/nearby_share_app).
Install it on two phones for direct phone-to-phone transfer, or use the
GitHub-Pages-ready browser launcher in [`tools/nearby_share_web`](tools/nearby_share_web)
on one device and the Nearby Share app on the other. Both devices must be on
the same Wi-Fi or hotspot; the static site does not relay files.
