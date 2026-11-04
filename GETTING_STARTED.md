# Setup and first test

Download the beta ZIP from **Releases**, unzip it, move NDock.app to Applications, and open it. If macOS blocks the download, report the message.

For the first test, use a few non-sensitive JPEG/NEF files and a new local destination folder. Report whether installation, pairing, and import each succeeded.

## 1. Prepare the camera and network

Use a powered-on Nikon Z8 with a memory card containing a few JPEG or NEF photos. Connect the Mac to the local network you intend to use with the camera.

The tested setup uses a router. The camera and Mac must be able to reach each other on that local network. Guest-network or device-isolation settings can prevent discovery even if both devices have internet access.

For the initial connection, use NDock as the camera's computer client. Close other camera-control/transfer applications that may try to use the same camera session.

## 2. First pairing through a router

Skip to [reconnecting](#3-reconnecting-a-paired-camera) if this camera already has a working NDock profile.

On the Z8:

1. Open **Network menu → Connect to computer → Network settings**.
2. Choose **Create profile** and give the profile a recognizable name, such as `NDock`.
3. Choose **Search for Wi-Fi network** and select your router's network.
4. Enter the network password on the camera and complete its IP-address setup; use automatic addressing if that matches your network.
5. Continue to the computer-pairing screen. Nikon's camera wizard may prompt you to start Wireless Transmitter Utility. NDock supplies its own pairing workflow: use NDock for the following steps.

On the Mac:

1. Open NDock. It starts searching for cameras automatically.
2. Allow local-network access when macOS requests it.
3. Select the camera in the upper camera menu if necessary. The main action changes with the camera state; choose **Pair camera…** when it is offered. Pairing is also available in the **•••** menu for a camera in pairing mode.
4. When NDock requests the four-digit camera code, enter the code displayed on the camera and confirm **Pair camera**. The code belongs in NDock, not in a log or problem report.
5. Complete any confirmation still shown on the camera. Keep the profile selected.

Finally, on the camera choose:

**Network menu → Connect to computer → Connection type → Camera control**

NDock needs **Camera control** to browse and select existing card photos from the Mac. **Picture transfer** is a different camera-selected upload workflow.

Return to NDock and let discovery continue. If necessary, choose **Find camera**, then **Connect camera** when offered. Once the camera is available in Camera Control mode, NDock normally opens its catalog automatically.

NDock retains its own pairing identity. A profile created for another application should not be assumed to be an NDock pair; use a dedicated profile for NDock. If the camera reports success but NDock does not connect, check that both devices are on the same network and report the final status in Issues.

## 3. Reconnecting a paired camera

1. Turn on the camera and select its saved NDock network profile.
2. Confirm that **Connection type** is **Camera control** and that the Mac is on the reachable local network.
3. Open NDock. It searches automatically and connects to a single or remembered Camera Control camera.
4. If several cameras are listed, choose the intended camera in the upper menu. Use the main **Connect camera** action when offered.
5. If automatic recovery previously ended, restore the camera's connection and click **Find camera**.

The saved identity is reused; a code is not normally needed for each connection. If a copy was interrupted, reconnecting and resuming that saved queue are separate actions: use **Resume** after the camera is available.

## 4. Understand the catalog status

| Status | Meaning |
|---|---|
| **Cached · updating** | A previous complete catalog is available for browsing while NDock reads the camera again. |
| **Cached · changes detected** | The fresh inventory or metadata differs; NDock is refreshing the catalog. |
| **Up to date** | The current full catalog check completed. Each original is still checked before it is copied. |
| **Cached · not verified** | Refresh stopped or failed. Browse the saved view and use **Refresh library** to retry verification. |

New object identifiers and the last known objects on each card are checked first; the remaining metadata follows. Import and new preview requests wait for verification in build 93. Already-cached previews can be displayed while checking.

Catalog dates come from camera metadata (PTP ObjectInfo). They are not necessarily EXIF dates. A raw object count can include folders and is not always the number of importable photos.

## 5. Choose photos

- Click a date row to expand or collapse it. Previews are requested for visible photos when the camera is available for them.
- Use the card and format controls to narrow the catalog.
- Click the yellow magnifier beside **Select all**, or press **⌘F**, to search filenames. Clicking the magnifier again closes the field and clears that filter.
- Click a photo to select it. **⌘-click** toggles a photo; **Shift-click** selects a range among the currently expanded dates. **⌘Shift-click** adds a range to the existing selection.
- **Select day** selects all importable matching photos for that date, including those whose previews have not loaded.
- **Select all** applies to matching photos across all dates, including collapsed dates.
- Large dates show a bounded page first. Use the date's **Show … files** footer to display the next page.

Selected-file totals appear at the bottom. The Edit menu's **⌘A** selects text in an active text field; it does not select all camera photos.

## 6. Import originals

1. Wait for catalog verification to complete.
2. Click **Choose folder…** and select the destination.
3. Select photos and click **Import**.
4. Follow the saved-file count and the current file's byte progress. The yellow progress bar counts fully completed files.
5. Wait for **Copy completed**. Use **Show in Finder** to open the destination when available.

Files are copied as originals, not re-encoded. A temporary file is published under its final name after the transfer and size check complete. Existing destination files are not silently overwritten. Photos on the camera are retained.

You can change browsing filters and the destination for the next copy while an import is running. The active queue keeps its original files and destination.

## 7. Pause, resume, and connection loss

**Pause** finishes the current file and stops before the next one. While waiting for an automatic retry, Pause can stop that wait immediately. After pausing, the result shows **Paused by you** and an inline **Resume** button.

**Resume** verifies the camera, source files, and destination before continuing the saved queue. Completed files are kept. An unfinished file is restarted from its beginning; byte-offset continuation is not implemented.

When automatic retry is enabled, temporary connection failures retry the current unfinished file. The recovery status shows the attempt and remaining waiting window. If automatic recovery ends, restore the connection, use **Find camera**, and then **Resume** or the recovery options in **•••**.

NDock checks its local journal at startup. The **•••** menu provides **Check for interrupted copies…**, direct resume or a queue chooser when available, and queue review/discard actions. **Discard queue** keeps completed files but removes the unfinished queue from recovery.


Assistant is experimental. Start with Camera Control for the first test.
