The Genies Animation view/Composer view are added as fragments.

The parent activity must extend FragmentActivity and implement AndroidFragmentApplication.Callbacks.

```java
/**
 * Model class representing info about a genie character to be rendered on screen 
 */
public class GenieCharacterInfoModel {
     /**
     *
     * @param genieGender MALE / FEMALE
     * @param genieAnimation The animation that the Genie character should run. Pass null if no animation should be played
     * @param positionX The horizontal position of the Genie character on the canvas
     * @param positionY The vertical position of the Genie character on the canvas
     * @param sizeScale The sizeScale for Genie character's size
     * @param genieCharacterAnimationCallback Callback notifying when the animation attached to the Genie character finished playing.
     */
    public GenieCharacterInfoModel(AvatarDB.Gender genieGender, GenieAnimation genieAnimation, int positionX, int positionY, float sizeScale, GenieCharacterAnimationCallback genieCharacterAnimationCallback);
}
```

```java
/**
 * Helper class that manages an Animation View
 */
public class GeniesAnimationViewManager 
{
     public GeniesAnimationViewManager(FragmentManager fragmentManager);
    
    /**
     * Loads a GenieAnimationView instance into the supplied root layout id
     *
     * @param fragmentContainerId The root layout id where to place the GenieAnimationView fragment
     * @param genieCharacters     List of Genie Characters to show on screen
     * @throws IllegalArgumentException
     */
    public void showAnimationView(int fragmentContainerId, final ArrayList<GenieCharacterInfoModel> genieCharacters);
    
     /**
     * Loads a GenieAnimationView instance into the supplied root layout id
     *
     * @param fragmentContainerId The root layout id where to place the GenieAnimationView fragment
     * @param genieCharacter    Genie Character to show on screen
     * @throws IllegalArgumentException
     */
    public void showAnimationView(int fragmentContainerId, GenieCharacterInfoModel genieCharacter);
    
    /**
     * Add a Genie to the canvas
     */
    public void addCharacter(GenieCharacterInfoModel genieCharacterInfoModel);
    
    /**
     * Remove a Genie from the canvas
     */
    public void removeCharacter(GenieCharacterInfoModel genieCharacterInfoModel);
    
    /**
     * Removes the animation view from the screen
     */
    public void removeAnimationView();
    
}
```

```java
/**
 *  Helper class that manages a Composer view
 */
public class GenieComposerViewManager {
    public GenieComposerViewManager(FragmentManager fragmentManager);
    
     /**
     * Creates a ComposerFragment and adds it to the view specified with the fragmentContainerIdParameter
     * @param fragmentContainerId id of the parent view where the Composer fragment should be placed in
     * @param assetPackFilePath the path of the asset pack ZIP file
     * @param characterConfigurationJson - initial configuration for the character assets. Should be null for a new configuration
     */
    public void showComposerView(int fragmentContainerId, String assetPackFilePath, String characterConfigurationJson);
    
     /**
     * Removes the composer fragment
     */
    public void removeComposerView();
    
    /**
     * @return a Json String of the current character configuration
     */
    public String getCharacterCurrentConfigurationJson();
    
    /**
     * @return a Btimap object representing a snapshot image of the current canvas configuration
     */
    public Bitmap getCanvasSnapshot();
}
```

