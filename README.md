## Animation Spy (Roblox)

Animation Spy is a lightweight **LocalPlayer-only** tool that watches which animations your character *actually plays* and turns them into a clean, paste-ready list of **digits-only Animation IDs**. Instead of logging everything (including broken or inaccessible assets), it performs a quick validation pipeline so your results stay trustworthy and usable.

### Why it’s useful

Many “animation spy” scripts capture IDs that later fail due to permissions, missing assets, or invalid tracks. Animation Spy filters that noise by validating every discovered ID before it appears in the UI.

### How it works

When your Humanoid plays an animation, Animation Spy:

1. Extracts the **best numeric asset ID** (longest digit sequence).
2. Validates usability using a two-step check:

   * **Preload test** via `ContentProvider:PreloadAsync()` (availability/permission)
   * **Load test** via a **dummy `AnimationController` + `Animator`** (safe, doesn’t touch your humanoid)
3. Logs only IDs that pass—typically also rejecting “empty” tracks (e.g., `Length == 0`).

### Features

* **Logs only usable animations** (preload + load validation)
* Outputs **digits-only IDs** (any length), ready to paste
* **COPY** button per row (no auto-play)
* **COPY ALL** exports all rows as `Name : ID`
* **CLEAR** wipes the list and resets caches/queues
* Draggable window + resize grip
* **RightShift toggle** to hide/show the UI instantly

### Notes

* Intended for debugging and development workflows.
* **LocalPlayer-only** by design.
* “FE visibility” depends on the game’s animation replication behavior—this tool focuses on discovery and validation.

### Quick start

1. Execute the script as a LocalScript.
2. Perform actions in-game (run, jump, climb, emotes, tools, etc.).
3. Click **COPY** / **COPY ALL** to export IDs.
4. Use **CLEAR** to reset and start a fresh capture session.
