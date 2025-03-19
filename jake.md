```markdown
*# Phase 1: Core Video Playback Setup*

## Core Objective
Establish the foundation for video playback using libmpv and integrate it with the existing PyQt5 UI.

## Key Steps
1. **Set up project environment** — *VALIDATED*
   - Install required dependencies (PyQt5, python-mpv)
   - Create main application entry point
   - Load the existing UI file (anaprev.ui)

2. **Implement basic MPV integration** — *VALIDATED*
   - Create a wrapper class for libmpv
   - Connect MPV to the script
   - Implement basic error handling for video loading

3. **Test basic video loading** — *VALIDATED*
   - Implement file selection dialog
   - Load and display a video file
   - Verify video appears in the movieScreen QWidget

## Validation Criteria
- Successfully load and display a video file
- Confirm video appears in the designated QVideoWidget
- Verify no crashes or major performance issues


## Next Steps
If validation succeeds, proceed to Phase 2 for playback controls.

---

*# Phase 2: Playback Controls*

## Core Objective
Implement basic video playback controls and timeline functionality.

## Key Steps
1. **Connect UI controls to MPV** — *VALIDATED*
   - Implement play/pause functionality
   - Implement stop functionality
   - Connect timeline slider to video position 

2. **Add time display** — *VALIDATED*
   - Update the LCD time display with current playback position
   - Format time display appropriately (HH:MM:SS:FF)

3. **Implement basic keyboard shortcuts** — *VALIDATED*
   - Add keyboard shortcuts for play/pause (C)
   - Add keyboard shortcut for play (X)
   - Add keyboard shortcut for stop (V)

## Validation Criteria
- Play/pause button toggles video playback
- Stop button halts playback and resets position
- Timeline slider shows and controls current position
- Time display updates correctly during playback
 *VALIDATED*

## Next Steps
If validation succeeds, proceed to Phase 3 for desqueeze functionality.

---

*# Phase 3: Desqueeze Implementation*

## Core Objective
Implement video desqueezing functionality to correct anamorphic footage.

## Key Steps
1. **Research MPV desqueeze options** — *VALIDATED*
   - Investigate libmpv parameters for aspect ratio control
   - Determine the best approach for real-time desqueezing

2. **Implement desqueeze factor option** — *VALIDATED*
   - Connect the squeeze factor radio button to functionality
   - Implement the dropdown selection for preset factors (1.3x, 1.6x, etc.)
   - Apply the selected factor to the video display

3. **Implement custom aspect ratio option** — *VALIDATED*
   - Connect the aspect ratio radio button to functionality
   - Implement width/height input fields
   - Calculate and apply the custom aspect ratio to the video

## Validation Criteria
- Switching between desqueeze options works correctly
- Preset factors (1.3x, 1.6x, etc.) visibly affect the video display
- Custom aspect ratio inputs correctly modify the video display
- Changes apply in real-time during playback
```