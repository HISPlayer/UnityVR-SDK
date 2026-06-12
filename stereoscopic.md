# Stereoscopic Video

HISPlayer SDK supports stereoscopic Side-By-Side (Left/Right) and Top/Bottom video rendering. **MV-HEVC** video codec is also supported with maximum resolution 1080p for smooth playback. 

There are 2 ways to render stereoscopic video depending on the selected **Render Mode**.

## External Surface Render Mode
If you use **External Surface** Render Mode in HISPlayer multistream properties, please use below API in your script:
#### void SetStereoscopicRendering(int playerIndex, HISPlayerStereoMode stereoMode, ref bool overrideRect, ref Rect srcRectLeft, ref Rect srcRectRight, ref Rect destRectLeft, ref Rect destRectRight)
Set stereoscopic rendering side by side or top/bottom. Only supported with external surface rendering mode. You may call this API after calling **SetUpPlayer** API. The parameters marked with ref keyword can be retrieved from public properties such as OVROverlay for Meta Quest. Usage example: 
```
SetStereoscopicRendering(streamIndex, HISPlayerStereoMode.LeftRight, ref overlay.overrideTextureRectMatrix, ref overlay.srcRectLeft, ref overlay.srcRectRight, ref overlay.destRectLeft, ref overlay.destRectRight);
```

## Material / RenderTexture / RawImage Render Mode
If you use **Material** or **RenderTexture** Render Mode in HISPlayer multistream properties, after creating your RenderTexture and Material, please attach **HISPlayerStereoscopicShader** shader to your Material.

Set the 3D Layout option to **Left Right** or **Top Bottom** depending on your stereoscopic video format.

<p align="center">
  <img width="70%" alt="image" src="https://github.com/user-attachments/assets/04e2dbdf-d102-4e42-b0f6-acb50799444e">
</p>

If you use **RawImage** Render Mode, please attach the Material with HISPlayerStereoscopicShader above to the material attribute of the RawImage component.

<p align="center">
  <img width="70%" alt="image" src="https://github.com/user-attachments/assets/29d98b03-edc3-4008-8ba5-19109e2fc150">
</p>
