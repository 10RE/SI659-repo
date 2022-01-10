# HTML/CSS

Set to `position: fixed` and place them at the bottom and the right using flexbox.

```css
#sidebar {
    display: flex;
    flex-direction: vertical;
    align-items: center;
    position: fixed;
    top: 0;
    right: 0;
    height: 100vh;
}

#toolbar {
    display: flex;
    flex-direction: row;
    justify-content: center;
    position: fixed;
    bottom: 0;
    left: 0;
    width: 100vw;
}
```

![image-20220110135827891](C:\Users\Lore_\AppData\Roaming\Typora\typora-user-images\image-20220110135827891.png)



# JS

Use `addEventListener`. For the behavior of drop down menu, the logic is when user leave the dropDown button for a while, the menu disappears, but when user leaves the dropDown button and enter the dropDownMenu, it won't disappear. If user then leave the dropDownMenu, the menu will disappear.

```javascript
let isOnDropDownMenu = false;
let menu = document.querySelector("#menu");
let dashboard = document.querySelector("#dashboard");
let toggleMenu = document.querySelector("#toggle-menu");
let dropdown = document.querySelector("#dropdown");
let dropdownMenu = document.querySelector("#dropdown-menu");

dashboard.addEventListener("click", () => {
    window.location.reload(true);
})

toggleMenu.addEventListener("click", () => {
    if (menu.style.display === "none") {
        menu.style.display = "inline";
    }
    else {
        menu.style.display = "none";
    }
});

dropdown.addEventListener("mouseenter", () => {
    dropdownMenu.style.display = "inline";
})

dropdown.addEventListener("mouseleave", () => {
    if (!isOnDropDownMenu) {
        setTimeout(() => {
            if (!isOnDropDownMenu) {
                dropdownMenu.style.display = "none";
            }
        }, 500);
    }
})

dropdownMenu.addEventListener("mouseenter", () => {
    isOnDropDownMenu = true;
})

dropdownMenu.addEventListener("mouseleave", () => {
    isOnDropDownMenu = false;
    setTimeout(() => {
        if (!isOnDropDownMenu) {
            dropdownMenu.style.display = "none";
        }
    }, 500);
})
```



# A-Frame

missing `<a-cylinder>`, `<a-entity>` property seems not correct.

```html
<a-scene stats background="white">
      <a-sphere position="0 1.25 -5" radius="1.25" color="red" shadow></a-sphere>
      <a-entity geometry="primitive: box" position="-1 0.5 -3" rotation="0 45 0" width="1" height="1" depth="1" material="blue" shadow></a-entity>
      <a-cylinder position="1 0.75 -3" radius="0.5" height="1.5" color="yellow" shadow></a-cylinder>
      <a-plane position="0 0 -4" rotation="-90 0 0" width="4" height="4" color="teal" shadow></a-plane>
      <a-sky color="silver"></a-sky>
</a-scene>
```

![image-20220110152933003](C:\Users\Lore_\AppData\Roaming\Typora\typora-user-images\image-20220110152933003.png)



# Unity

This script makes the game object move in constant speed on x axis.

There should be problem as the `originalPosition` and `TargetPosition` is not assigned an initial value.
