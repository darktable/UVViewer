# UV Viewer for Unity Editor
UVViewerWindow is an editor window extension class that allows you to check the mesh's UV in the Unity editor. Unity 5.4 or higher is required.

![](Screenshot.png)

## installation
If you download and import the Unity package from the [Release page](https://github.com/songkyoo/UVViewer/releases) or copy the [Assets/Plugins](Assets/Plugins) folder to your project, the UV Viewer is added. When you execute the item, an editor window is created.

## How to use
### mesh settings
If the Mesh item is Selected Object, if you select a game object that includes mesh or MeshFilter and SkinnedMeshRenderer components, UV is displayed.

If you set the Mesh item to Custom, you can set the mesh yourself. Dragging and dropping an object into the view area will do the same. Draggable objects are meshes or game objects that contain MeshFilter and SkinnedMeshRenderer components.

### Texture Settings
If the Mesh item is Selected Object, if the selected game object includes MeshRenderer or SkinnedMeshRenderer components, if you set the Texture item to Materials, you can select the texture of the material included in the renderer.

You can set the texture yourself by setting the Texture item to Custom. Dragging and dropping a texture into the view area does the same thing.

### access from editor script
You can set meshes or textures created from editor scripts. The following code sets values ​​to the window being displayed if the window is visible, or creates a new window and sets the values ​​to it if there is no visible window.

```csharp
using Macaron. UVViewer. Editor;

class EditorClass
{
    void SetCustom(Mesh mesh, Texture texture)
    {
        // mesh settings.
        UVViewerWindow.ShowWindow().SetCustomMesh(mesh);

        // Texture settings.
        UVViewerWindow.ShowWindow().SetCustomTexture(texture);
    }
}
```

If you call the `SetCustomMesh` or `SetCustomTexture` methods, the Mesh and Texture items are changed to Custom, and the Source is set to the called value. Each method can be called individually.

## Restrictions
1. Visible UVs and textures do not automatically reflect changes to the original. If you need to update, you need to reload it by pressing the Reload button in the Mesh and Texture items.

2. If the Geometry shader is not supported, the Line Thickness item will not be available and the view area will be displayed in low resolution in HiDPI environment.