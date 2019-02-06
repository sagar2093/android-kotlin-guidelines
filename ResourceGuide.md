## Layout
Layout files should match the name of the Android components that they are intended for but moving the top level component name to the beginning. For example, if we are creating a layout for the **SignInActivity**, the name of the layout file should be `activity_sign_in.xml`.

A slightly different case is when we are creating a layout that is going to be inflated by an **Adapter**, e.g to populate a **ListView** or **Recyclerview**. In this case, the name of the layout should start with `item_`.

![](https://cdn-images-1.medium.com/max/800/1*E2CNQ6wxVwBS1fBvQzfPzQ.png)
 *Example of layout resource file*
 
## Strings
String names start with a prefix that identifies the section they belong to. We use <HOW>_<DESCRIPTION> for strings naming. <HOW> to indicate reason of the string will be used & description give any extra information.

For ex:

<string name="label_home">Home</string> : how = label & home is description of the string.
<string name="hint_user_name">Enter Your Name</string> : how = hint & user_name is the description of string.

## Drawables
We use <WHAT>_<DESCRIPTION> for strings naming. <WHAT> is Button,Dialog,Divider,Icon, etc & description give any extra information.

![](https://cdn-images-1.medium.com/max/800/1*YrWmzRSvz9BWosoE5Qtykg.png)
 *Example of drawable naming*
 
## Dimensions
Apps should only define a limited set of dimensions, which are constantly reused.

<WHAT>_<WHERE>_<SIZE> :

<WHAT> : It can be width(in dp), height (in dp), size (if width == height), margin(in dp), padding(in dp), elevation(in dp). text_size(in sp).
<WHERE>: It can be any specific item or remove this section if used throughout the application.
<SIZE>: It can be dp or sp.

![](https://cdn-images-1.medium.com/max/800/1*66JEKhu7WqtPMkjegXMmgQ.png)
*Example of dimenstions*

### References
1. https://medium.com/mindorks/android-resource-naming-convention-42e4e8026614
2. https://jeroenmols.com/blog/2016/03/07/resourcenaming/
3. https://github.com/ribot/android-guidelines/blob/master/project_and_code_guidelines.md
