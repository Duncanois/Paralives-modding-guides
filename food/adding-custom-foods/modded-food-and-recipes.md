# Adding working custom food & recipes *(Youtube link coming later)*
## Index
<List of content and navigation here>
Paralives official Discord link: https://discord.gg/paralives
*Note: This tutorial currently covers the methods to get a modded recipe recognised and usable within the game. Skin meshes currently incorrectly or do not get their detail map applied due to the Surface property missing from selection on new entries. We may be able to get around this by relying on texturing the meshes directly. If I find this works, I will update my tutorial accordingly.*

**This guide assumes you understand the basics of the Paralives modding suite and 3D modelling. If you need help, I or others will have text and video guides on these topics, or if you prefer you can ask me here directly:** https://discord.com/channels/595045400805769238/1514044021411025039
**This tutorial may be adjusted for neatness and new information if needed.**
*The screenshots may not be completely neat, but it should be clean enough for the sake of this written guide.*

## Step 1: Asset setup
### Folder setup
![alt text](Paralives_Modding_Folder_Food-2.png)
![alt text](Paralives_Modding_Folder_Food_Pancake_Pizzas.png)
![alt text](Paralives_Modding_Folder_Food_Steps.png)
- Within your mod's files, create a new folder named `Environments` (You can quickly open the relevant Paralives folder by searching this in Windows directly: `%userprofile%\AppData\LocalLow\Paralives\Paralives\`). Winthin Environments, create another folder named `Items` and within Items `Food`.
- Inside the Food folder, create the folders `Steps`, `Thumbnails` and any other folders named after your food items. I named my demostration item `PancakePizzas`, but the name is not necessary for functionality (*Naming the folders Steps and Thumbnails is not crucial for the game to read them, but doing this this is a good habit as it helps keep things organised and speeds up outside assistance if you need it.*).

### File types needed
You will need two file types: FBX and PNG.
- FBX: 1-6 for your food mesh.
- PNG: 1-6 for the detail map.
- (Optional) PNG: 1 for custom/styled menu thumbnail (it is necessary for now as without Surfaces the recipe icon does not generate in the menu at all).
You need at minimum the mesh for your finished food item and the detail map to texture it. 
There are 2 mesh variations for group meals (**full, half**) and 4 with indivdual (**full, half, full-in-hand, half-in-hand**). 
You only require 1 detail map for both group and individual meals, but adding texture for each different mesh can be done if you want a specific look for each variation.
You can also add your own recipe step meshes and maps (such as eggs and flour or batter), but vanilla comes with many detailed assets already made for this purpose. You can use vanilla animations or rig your own, but for this tutorial we'll use vanilla steps and animations. I'll be making an advanced guide later for adding animations and multi-step individual stages (such as for making a 3-tier cake), but those are more advanced concepts and once surfaces are working I'll make the tutorial for it.

### Folder setup
Within your mod's files, create a new folder named `Environments` (You can quickly open the relevant Paralives folder by searching this in Windows directly: `%userprofile%\AppData\LocalLow\Paralives\Paralives\`). Winthin Environments, create another folder named `Items` and within Items `Food`.
Inside the Food folder, create the folders `Steps`, `Thumbnails` and any other folders named after your food items. I named my demostration item `PancakePizzas`, but the name is not necessary for functionality (*Naming the folders Steps and Thumbnails is not crucial for the game to read them, but doing this this is a good habit as it helps keep things organised and speeds up outside assistance if you need it.*).
#### Folder explanation:
- **Environments** is the default vanilla directory/folder for Paralives, and holds all art assets, for example meshes, maps and prefabs.
- **Items** is the container for all interactable and visual objects in game, from computers to clutter to food.
- **Food** holds the mesh and detail maps for cooking assets and functional foods.
- **Food types** are individually named folders for categorising food assets. As said, these can be named anything, but should be descriptive of the meal for legibility (for example "Cakes").
- **Steps** is for the visual cooking process, such as taking cake batter from the fridge.
These folders are merely cosmetic in reality, but it's good practice to keep them organised and tidy.

#### Recommended structure:
![alt text](Paralives_Modding_Folder_Food-3.png)
![alt text](Paralives_Modding_Folder_Food_Pancake_Pizzas-1.png)
![alt text](Paralives_Modding_Folder_Food_Steps-1.png)
![alt text](Paralives_Modding_Folder_Food_Thumbnails.png)

## Step 2: Adding visuals and functionality
### Categories
There are only two categories needed for full functionality:
#### Skins
Required for visual functionality of the entire meal system.
#### Skills
Necessary to see and cook recipes in the Cook menu. There are very few entries you will make here compared to Skins and is more straightforward.

### Initial functionality setup
#### Setting recipe menu visibility and skill level requirements
You only need to touch 2 categories: **Skins** and **Skills**.
![alt text](<Screenshot 2026-06-12 121211.png>)
1. Create your food entries. You need at minimum Meal_MyFood_Indivdual, CookingStep_MyFood, and if it's a group meal add Meal_MyFood_Group to these items.
If your food can be cooked as both individual and group servings, another entry and name it CookingStep_MyFood_Individual.
Creating additional Cooking Steps will allow you to add modded ingredients, cooking utilities or visual cooking stages (such as a cake rising when it's finished cooking), but this will not be explaining in this tutorial.
![alt text](<Screenshot 2026-06-12 124540-1.png>)
For the purpose of this tutorial we will use the required entries to create a group meal, as well as adding our modded ingredient. These are repurposed vanilla assets but are suitable for demonstration.
![alt text](<Screenshot 2026-06-12 131301.png>)
2. The Skills Cooking category only needs to be touched if you wish for your recipe to show up by default. If you do not want to do this and prefer for it to show up through gameplay, you can skip this step. Recipes not set in this way will show up through regular gameplay, either by leveling up the Cooking skill or discovering recipes through the computer etc.
To automatically unlock this recipe for a Para when loading into a save, add it to one or more Initial Skins Packs. This will give it along with the other recipes in the selected pack to a new or existing Para. Adding it to more or all of the other packs will increase the chances of a Para having it by default.
![alt text](<Screenshot 2026-06-13 103002.png>)
You can also give it as an extra/bonus starting recipe for certain personality traits, such as having the Food Talent. There's a lot more possibilities but this tutorial will not cover them.
![alt text](<Screenshot 2026-06-13 104335.png>)
3. Go back to the Skins category.
For each meal, You will add to the Parent Skins. In the screenshot the format is set out for you. You can set the recipe level to whatever you want, but make sure you have "_Single" and "_Group". If your recipe is a single serving meal, you will only need _Single. If a group meal, set to _Group.
If your meal has a group serving, make sure you also add the individual version (Meal_PancakePizza_Individual in our example)
**Make sure you click Is Visible In Skin Selection Menu, otherwise your meal won't show up in the Cook menu.**
![alt text](<Screenshot 2026-06-13 105024.png>)

### Setting meal visual properties and functionality
#### Tip: Using vanilla recipes as examples
A good tip is to use vanilla recipes for the cooking process that are similar to what you want.
For example, since we are creating a pizza, we will use one of the vanilla pizzas as a basis for our meal:
**Note: We do not look at Parent Skins as that was already set up in Step in Step 3 of the previous section.**
_Vanilla Piza (Individual)_
![alt text](<Screenshot 2026-06-14 170250.png>)
_Vanilla Piza (Individual) properties (1/2)_
![alt text](<Screenshot 2026-06-14 165424.png>)
_Vanilla Piza (Individual) properties (2/2)_
![alt text](<Screenshot 2026-06-14 165535.png>)

_Vanilla Piza (Group)_
![alt text](<Screenshot 2026-06-14 170213.png>)
_Vanilla Piza (Group) properties (1/2)_
![alt text](<Screenshot 2026-06-14 165710.png>)
_Vanilla Piza (Group) properties (2/3)_
![alt text](<Screenshot 2026-06-14 165915.png>)
_Vanilla Piza (Group) properties (3/3)_
![alt text](<Screenshot 2026-06-14 170038.png>)

#### Setting your food as a recipe
There are only two things you have to do here.
1. Set `Skin Type` to **Recipes**
2. Click and set `Is Visible in Skin Selection Menu` to enable it for cooking. Do this for Group, Individual or both depending on portion sizes your meal should be available in.
_Individual_
![alt text](<Screenshot 2026-06-14 191054.png>)
_Group_
![alt text](<Screenshot 2026-06-14 190350.png>)

#### Explanation of important Skin Properties
_Surfaces property will be empty due to the bug, so ignore that in your modded food for now._
_Decal Map is not relevant and will be ignored, as this is for dirty surfaces, broken objects etc._
**This covers the basic outline of Skin Properties. I may or may not add a breakdown of all options found in each property at a later stage.**

**Individual**
1. DisplayName:
The name of your recipe will show up with the String Value of the DisplayName property.
It is good practice to set the exact name you want to show up in the menu, and it also avoids potential issues with the name appearing in game. To do this click the symbol next to the String Value field:
_This should only be set for the individual serving. Do not set for the group option._
![alt text](<Screenshot 2026-06-14 171821.png>)
A new window will pop-up in game. The only thing you need to edit here is the "Translated text" box. It will start empty. This should be the name of the actual meal.
![alt text](<Screenshot 2026-06-14 171308.png>)
2. Plate:
This is the type of plate your food will appear on after cooking.
You can look at a vanilla meal if you want to see what plate works best for you. You can also add your own plate meshes, but that requires further setup that will not be covered in this tutorial yet, but you can send me a message on Discord if you want to know how to do it now.
![alt text](<Screenshot 2026-06-14 172357.png>)
3. Meal:
The actual appearance of the cooked meal.
Mesh is the FBX file of the food you will use. If the actual meal is a group serving, use the single portion variation if you have.
Detail Map is the PNG of the texture as discussed at the beginning. Can be used for both Individual and Group.
![alt text](<Screenshot 2026-06-14 172337-1.png>)
4. MealHalfEaten:
The change in appearance when half of the serving has been eaten.
![alt text](<Screenshot 2026-06-14 173217.png>)
5. MealInHand:
_(Ensure this is only set for individual, not group meal servings)_
How the food appears on the plate, as well is in the hand if the animation is set as such.
![alt text](<Screenshot 2026-06-14 173615.png>)
6. MealInHandAndHalfEaten:
Same as MealHalfEaten, but instead the appearance of the food while it is actively eaten.
You can usually have this set to the exact settings as MealHalfEaten, such is for a cake.
![alt text](<Screenshot 2026-06-14 173659.png>)
7. EatingAnimation:
The animation and objects used when eating the meal. For example, setting it to EatingSlice will have the Para pick it up off the plate, while EatPlateFork will use a fork when eating from the plate.
![alt text](<Screenshot 2026-06-14 174138.png>)
8. CookingSteps:
Can be set in either Individual or Group meal Skins.
If the meal has an option to cook both a group serving and a single serving, you can set it it here if the cooking process is the exact same for both. If you do this, you do not need to set it in the Group (setting it in Group will not cause any issues, but it will take unnecessary extra time to setup your food if the process is the same).
_Covered in Group explanation below, but this must also be set if the meal has a single serving option._
9. Thumbnail:
Set this for the serving option or options that will be available to cook. 
_Example shown in Group below, as the Pancake Pizza is a group-only recipe._

**Group**
1. Plate:
This is the type of plate your food will appear on after cooking.
Look at a similar vanilla **Group** portion to see what works.
![alt text](<Screenshot 2026-06-14 175053.png>)
2. Meal:
The actual appearance of the cooked meal. This is the group serving version.
Detail map can be used for both Individual and Group.
![alt text](<Screenshot 2026-06-14 175530.png>)
3. MealHalfEaten:
The change in appearance when half of the serving has been eaten.
![alt text](<Screenshot 2026-06-14 175617.png>)
4. SinglePortion:
The _Individual meal you created earlier. The game will use this as the single serving that will be taken from the group meal.
![alt text](<Screenshot 2026-06-14 202402.png>)
5. CookingSteps & Skinned Steps:
The actual cooking process, from getting ingredients, to preperation and the final cooked meal.
Individual CookingStep entries will be added to Skinned Steps.
_(The actual amount of Skinned Steps you use will probably differ, as this example is for my Pancake Pizza)_
![alt text](<Screenshot 2026-06-14 180107.png>)
6. CookingStep:
The individual stages of the recipe's progress.
Created by adding a new entry to Skinned Steps and setting Tag to CookingStep.
- Catalogue Item: The visual stage of the recipe. filter your search by `foodsteps` to find the exact items used in recipes. Most will be animations (they will have "Anim" at the end) but some are not directly animations as they are static (Such as FoodStepsFlourCounter). I will explain how this works in Action Unit. 
_(Some vanilla Catalogue Items may look out of place for your food, especially noticeable when you complete the last stage of the recipe as it changes from the vanilla ingredient directly to your food. When the Surfaces bug is fixed, I will update this guide to show how to add a Catalogue Item to fit the look of your meal, including how to reuse and adjust existing vanilla items to better suit your needs.)_
- Action Unit: This is how the game understands what to do at this recipe stage.
- Skin References: The visual item and/or ingredient that will be used at this stage, which is set in the Value field after adding an entry (search directly for `foodsteps` to quickly find related objects).
_In most cases you will only add one entry, but you can also add more if your ingredients go through a visual change once this CookingStep is done (such as a having a cake rise fully after it is completed). I will explain in a future edit of this tutorial._
**IMPORTANT:** The Skin Reference _before_ the final CookingStep must **always be your custom CookingStep_MyFood.** This tells the game that you meal is fully cooked and must be converted into the completed meal once this stage completes.
Your final CookingStep entry in Skinned Steps must only have Action Unit, and this must be set to `CreateFood`. Leave Catalogue Item and Skin References empty or None. It will look exactly like this for every meal/recipe:
![alt text](<Screenshot 2026-06-14 180442.png>)
*(CookingStep_MyFood will be explained after the Pancake Pizza screenshots below).*

Pancake Pizza Cooking Steps:
![alt text](<Screenshot 2026-06-14 185736.png>)
_Step 1_
![alt text](<Screenshot 2026-06-14 185043.png>)
_Step 2_
![alt text](<Screenshot 2026-06-14 185351.png>)
_Step 3_
![alt text](<Screenshot 2026-06-14 185432.png>)
_Step 4_
![alt text](<Screenshot 2026-06-14 185500.png>)
_Step 5_
![alt text](<Screenshot 2026-06-14 185707.png>)

9. Thumbnail:
Set this for the serving option/options that will be available to cook.
![alt text](<Screenshot 2026-06-14 195258.png>)

_There are other properties you can set to add specific behaviour to your meal, such as flagging it as Vegetarian, disabling the steam effect for stove/microwave/grill recipes and others. I'll do that in another tutorial._

#### Modded CookingStep_MyFood setup
*If you have group and single servings as options for cooking, ensure you created CookingStep_MyFood_Individual and do the following for both.*
1. Set Skin Type to FoodSteps.
2. You only need to add `CookingStepVisual` to the Skin Properties here.
- Mesh: Your finished meal.
- Detail Map: Your finished meal.
![alt text](<Screenshot 2026-06-14 185818.png>)

## Step 3: Testing your food and recipe in-game
_(For modding in general, I highly suggest creating a new game using the Simple Empty Terrain map option. This greatly speeds loading times, which helps with testing mod features after any changes. For this tutorial, it cuts loading times in a save from almost two minutes in an existing save to less than 5 seconds. Just make sure to save the world immediately after creating you test Paras and setting up your test house or objects! Create a backup after this, and avoid saving when quitting unless you need to as having a clean slate between tests is beneficial. You should always return to the main menu whenever you work on your mod, as using the mod control panel in game will not always be reliable for testing.)_
1. _If you have set your recipe for all Cooking Initial Skins Packs or Extra Initial Skins Packs, you can skip to step 2 if clicking Cook on the fridge has your recipe displayed already._
Hit Ctrl+Shift+C to open the commands/cheat window. Inside, copy and paste `LEARNALLSKINS recipes`. You will get a replay saying the number of "skins of type recipes learned". The number it shows should be ignored usually, as learning recipes through play time and new food updates/mods will change the number it shows.
If you have done the tutorial correctly, you will see your food here, categorised by level:
![alt text](<Screenshot 2026-06-14 201059.png>)
2. This next part will likely vary completely in your mod compared to my cooking process, so I won't go over my pancake pizza directly, but make sure to confirm the recipe cooks with the expected steps. Some recipes, such as exotic foods may require more trial-and-error to get the correct animations, visuals etc. 
Be sure to test the group and single sizes, the half-eaten changes   . If the Para is eating it, the meal is working successfully and will fill the Hunger need bar. If you want to be certain, look for green face icon next to the bar. This confirms the meal is recognised as food, and will show up even if eating when full:
![alt text](<Screenshot 2026-06-14 204949.png>)
### Critical reminder before finishing
This section will be removed when the Surfaces bug is fixed, but for now this is to get your food working. When that bug is fixed, all you will need to do is go to the Skin Properties of your Individual and Group entries that have Mesh fields and change only the "Surface" category within Surfaces to your desired option (I recommend using the vanilla GenericFoodSurface, as it is universal for all meals and is recommended to use). When fixed, it will look like this:
![alt text](Surfaces_None_Example-1.png)
Unfortunately, this means that without being able to add a surface, the detail map will not generate, and your meal's meshes will appear with their default flat texture. We prepared the detail maps in advance as they will be needed when this issue is fixed.
**You might be able to bypass this issue by texturing your FBX files first, but make sure you keep a flat version when the detail map works.**
_MelancholicSound.ogg_
![alt text](<Screenshot 2026-06-14 201352.png>)
![alt text](<Screenshot 2026-06-14 212255.png>)

## I hope this helps you, and thank you for stopping by 🙂