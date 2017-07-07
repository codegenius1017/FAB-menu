# FloatingActionButtons Menu (FABsMenu)

[![JitPack Badge](https://jitpack.io/v/jahirfiquitiva/FABsMenu.svg)](https://jitpack.io/#jahirfiquitiva/FABsMenu)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/3ab596acdd5648599c34d56dba1eea39)](https://www.codacy.com/app/jahirfiquitiva/FABsMenu?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=jahirfiquitiva/FABsMenu&amp;utm_campaign=Badge_Grade)
[![Build Status](https://travis-ci.org/jahirfiquitiva/FABsMenu.svg?branch=master)](https://travis-ci.org/jahirfiquitiva/FABsMenu)

Just a simple library to use a menu with `FloatingActionButton`s from Design Support Library and following [guidelines](https://material.io/guidelines/components/buttons-floating-action-button.html#buttons-floating-action-button-transitions)


## Preview

![FABs Menu Preview](https://github.com/jahirfiquitiva/FABsMenu/raw/master/preview/preview.gif)


## Usage

Add jitpack dependency to your root `build.gradle`:
```groovy
allprojects {
    repositories {
        maven { url 'https://jitpack.io' }
    }
}
```

Next, add the dependency to your `build.gradle`:
```groovy
dependencies {
    compile 'me.jahirfiquitiva:FABsMenu:1.0.0'
}
```

Then sync the gradle files.

Finally, use it in your layout, just like this:

To see how the buttons are added to your xml layouts, check the sample project.


```xml
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
                xmlns:fab="http://schemas.android.com/apk/res-auto"
                android:layout_width="match_parent"
                android:layout_height="match_parent">

	<!-- Menu Layout is needed for the overlay to work -->
    <jahirfiquitiva.libs.fabsmenu.FABsMenuLayout
            android:layout_width="match_parent"
            android:layout_height="match_parent"
			fab:fabs_menu_overlayColor="#4d000000"
			fab:fabs_menu_cickableOverlay="true">
			
		<!-- FABs Menu is the main view. It will contain all the items FABs and it create the menu fab itself -->
        <jahirfiquitiva.libs.fabsmenu.FABsMenu
                android:id="@+id/fabs_menu"
                android:layout_width="wrap_content"
                android:layout_height="wrap_content"
                android:layout_gravity="bottom|end"
                android:clipChildren="false"
                fab:fab_menuMargins="16dp"
                fab:fab_moreButtonPlusIcon="@drawable/ic_plus"
                fab:fab_moreButtonBackgroundColor="@color/pink"
                fab:fab_moreButtonRippleColor="@color/pink_pressed"
                fab:fab_moreButtonSize="normal"
                fab:fab_labelsPosition="left"
                fab:fab_expandDirection="up">

			<!-- This is the item that appears at the top of the menu -->
            <jahirfiquitiva.libs.fabsmenu.TitleFAB
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    fab:srcCompat="@drawable/ic_share"
                    fab:fabSize="mini"
                    fab:backgroundTint="@color/colorAccent"
                    fab:rippleColor="@color/colorAccent"
                    fab:fab_title="This is a custom title"
                    fab:fab_title_backgroundColor="@color/colorAccent"
                    fab:fab_title_textColor="@android:color/white"/>

            <jahirfiquitiva.libs.fabsmenu.TitleFAB
                    android:id="@+id/clickable_title"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    fab:srcCompat="@drawable/ic_pencil"
                    fab:fab_title="Clickable title"
                    fab:fab_enableTitleClick="true"
                    fab:fab_title_textColor="@color/colorAccent"
                    fab:fabSize="mini"
                    fab:backgroundTint="@color/colorAccent"
                    fab:rippleColor="@color/colorAccent"/>

            <jahirfiquitiva.libs.fabsmenu.TitleFAB
                    android:id="@+id/mini_fab"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    fab:srcCompat="@drawable/ic_heart"
                    fab:fab_title="Mini fab with long text"
                    fab:fabSize="mini"
                    fab:backgroundTint="@color/blue_semi"
                    fab:rippleColor="@color/blue_semi_pressed"/>

			<!-- This item will appear just above the menu FAB -->
            <jahirfiquitiva.libs.fabsmenu.TitleFAB
                    android:id="@+id/green_fab"
                    android:layout_width="wrap_content"
                    android:layout_height="wrap_content"
                    fab:srcCompat="@drawable/ic_person"
                    fab:fab_title="Fab with even longer text that might not even fit in all the screens"
                    fab:fabSize="normal"
                    fab:backgroundTint="@color/green"
                    fab:rippleColor="@color/green_pressed"/>

        </jahirfiquitiva.libs.fabsmenu.FABsMenu>
		
    </jahirfiquitiva.libs.fabsmenu.FABsMenuLayout>

</RelativeLayout>
```


## Attributes explanation

1. FABsMenuLayout attributes:
	* `fabs_menu_overlayColor` --> Set the menu overlay color (Defaults to `#4d000000`)
	* `fabs_menu_cickableOverlay` --> Specify whether the overlay is clickable or not (Defaults to `true`)

2. FABsMenu attributes
	* `fab_menuMargins` --> The margins of the menu (Defaults to `16dp`)
	* `fab_moreButtonRippleColor` --> The menu fab ripples color
	* `fab_moreButtonBackgroundColor` --> The menu fab background color
	* `fab_moreButtonSize` --> Specify the size. Choose between `mini` and `normal` (Defaults to `normal`)
	* `fab_moreButtonPlusIcon` --> The reference to the plus icon drawable (Defaults to `null`)
	* `fab_labelsPosition` --> Where to show the labels. Choose between `left` and `right` (Defaults to `left`)
	* `fab_expandDirection` --> The direction the menu should expand to. Choose between `up`, `down`, `left` and `right`. (Defaults to `up`)
	
3. TitleFAB attributes:
	* `fab_title` --> A string that will be shown as the fab label (Defaults to `null`)
	* `fab_title_backgroundColor` --> The color of the label background (Defaults to `#fff`)
	* `fab_title_textColor` --> The color of the label text (Defaults to `#000`)
	* `fab_title_cornerRadius` --> The dimension of the label corners radius (Defaults to `2dp`)
	* `fab_title_textPadding` --> The dimension of the text padding (Defaults to `8dp`)
	* `fab_enableTitleClick` --> Specify whether the label click should fire the fab click too (Defaults to `false`)


## Important notes

1. The FABs are based on the ones from Design Support libraries, so you can use these customization attributes:
	```xml
		fab:fabSize="mini"
		fab:backgroundTint="@color/blue_semi"
		fab:rippleColor="@color/blue_semi_pressed"
	```
	
2. For the FABsMenu, the previous attributes will not work.
3. For the FABsMenu, use `fab_menuMargins` instead of the normal `android:layout_margin` attribute. This will prevent FABs elevation being cropped.
4. As stated in guidelines, a FABsMenu should not have more than 6 items. If you use more than 6, you will get an `IllegalArgumentException`. Also, remember FABs menu should have **at least** 3 items too.
5. For now, the icon you set for FABsMenu will always rotate, so be sure you set an icon that looks good in both states (normal and rotated).


## Credits

This project is based on Future Simple's [android-floating-action-button](https://github.com/futuresimple/android-floating-action-button) project, which is also based on [FloatingActionButton](https://github.com/makovkastar/FloatingActionButton) library by [Oleksandr Melnykov](https://github.com/makovkastar).


## License


    Copyright (c) 2017 Jahir Fiquitiva

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

         http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.


## Original license
	

    Copyright (c) 2014 Jerzy Chalupski

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

         http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
