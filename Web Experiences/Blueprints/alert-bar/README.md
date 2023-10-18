# Alert Bar
An alert bar that can be triggered top or bottom of your website.

![Alert Bar](alert-bar.gif)

## Quickstart
Copy the HTML/JS/CSS as needed from here to a new [Web Experience](https://documentation.boxever.com/docs/using-custom-code) in Boxever. Once created the following will be configurable components within the experience:
- Position
- Bar Colour
- Title Text
- Title Text Colour
- Title Text Font
- Title Font
- Button Text
- Button Colour
- Button Line Colour
- Button Text Font
- Button Link

You can add alertBarScroll.js to show after a certain scroll percentage.

### HTML
```html
<!-- Use dynamic Guest variables, type ctrl+space or guest to explore available entities.-->
<!-- Type "d" to see decisioning helpers -->
<div id="bx_TopBanner">
    <div class="bx_TopBanner__banner">
        <p class="bx_TopBanner__p">
            <span class="bx_TopBanner__p--span" style="display: inline;">[[Title Text | text | For this bar, we recommend less than 50 characters|  {max: 50 , group: Text Configuration}]]</span>
            <a id="bx_TopBanner-button" class="bx_TopBanner__p--button" href="[[Button Link | text |https://www.example.com/ | { group: Button Configuration ,required: false} ]]">[[Button Text | text | I accept | { group: Button Configuration }]]</a>
        </p>
        <div class="bx__btn-close"></div>
    </div>
</div>
```

### CSS
```css
/* accomodate every size screen by default */
/* tested on chrome, crome mobile, safari, firefox, edge */

/*
Declare Boxever Template Variables
[[Font | enum(Arial,Arial Narrow,Brush Script MT,Calibri,Cambria,Candara,Copperplate,Courier,Courier New,Didot,Garamond,Geneva,Helvetica,Lucida Bright,Monaco,Optima,Perpetua,Times,Times New Roman,Verdana) |Calibri| {group: General}]];
[[X Color | colour | #f88  | {group: Closing Button Configuration}]]
*/


/* The following Experience styling is populated with a unique variant identifier: { { ref } }
when deployed to ensure CSS does not impact styling of other elements. */

/* Hide original top banner (in case it"s present) */
.operational-updates {
    display: none !important;
}

/* Add this clase when "click" close icon */
.bx_TopBanner--hide {
    display: none !important;
}

/* Push content down to allocate top banner */
body.show-TopBanner {
    margin-top: 71px !important;
}

/* Banner styling (container) */
#bx-{{ref}} #bx_TopBanner {
    -webkit-box-shadow: 0px 0px 4px 0px rgba(9,9,9,0.4);
    -moz-box-shadow: 0px 0px 4px 0px rgba(9,9,9,0.4);
    box-shadow: 0px 0px 4px 0px rgba(9,9,9,0.4);
    min-width: 330px;
}

/* Banner styling (container) */
#bx-{{ref}} #bx_TopBanner {
    position: fixed;
    z-index: 99998;
    height: 71px;
    width: 100vw;
    [[Position | enum(Top, Bottom)| Top | { required: true, group: General } ]]: 0;
    background: [[ Bar Background Color | colour | #eeeeee| { group: General } ]];
    font-family: [[ Font ]]
}

/* Banner styling */
#bx-{{ref}} #bx_TopBanner .bx_TopBanner__banner {
    padding-left: 50px;
    padding-right: 50px;
    color: #000;
    margin: 0 auto;
    position: relative;
    height: 71px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

/* Text and button container  */
#bx-{{ref}} #bx_TopBanner .bx_TopBanner__p {
    margin: 8px 0;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 24px;
    width: 100%;
    line-height: 10px;
}

/* text */
#bx-{{ref}} #bx_TopBanner .bx_TopBanner__p--span {
    color: [[Title Text Colour | colour |#444| { group: Text Configuration }]];
    font-size: [[ Title Text Font Size | number | 18 | { group: Text Configuration }]]px;
    line-height: 16.1px;
    font-weight: 500;
    padding-right: 40px;
}

/* CTA button */
#bx-{{ref}} #bx_TopBanner .bx_TopBanner__p--button {
    border-radius: 4px;
    color: #fff;
    padding: 10px 23px;
    display: inline-block;
    min-width: 110px;
    text-align: center;
    cursor: pointer;
    border: none;
    margin-right: 10px;
    color: [[ Button Text Color | colour | #fff | { required: true, group: Button Configuration } ]];
    background-color: [[ Button Color | colour | #4caf50|{ required: true, group: Button Configuration } ]];
    font-size: [[Button Text Sixe in px | number | 16 | { group: Button Configuration } ]]px;
}

/* CTA Button on Hover */
#bx-{{ref}} #bx_TopBanner .bx_TopBanner__p--button:hover {
    box-shadow: 3px 4.9px 16px rgba(40,40,40,0.6);
    letter-spacing:2px;
    transform: scale(1.03);
    text-decoration: none !important;
}

/* closing Button on Hover, focus, active */
#bx-{{ref}} .bx__btn-close:hover,
#bx-{{ref}} .bx__btn-close:focus,
#bx-{{ref}} .bx__btn-close:active {
    background-color: transparent;
    box-shadow: none;
    color: #333;
    text-decoration: none !important;
    cursor: pointer;
}

/* close button */
#bx-{{ref}} .bx__btn-close {
    background: [[ X Background Color | colour | #fff|{ required: true, group: Closing Button Configuration } ]];
    top: 30%;  /* special size for alert bar */
    right: 20px;
    width: 30px;
    height: 30px;
    border-radius:15px;
    margin-top: 10px;
    margin-right: 10px;
    position: absolute;
    margin: auto;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
}

/* close button right side of X  */
#bx-{{ref}} .bx__btn-close:after {
    background: transparent;
    content: "";
    height: 20px;
    border-left: 2px solid [[ X Color ]];
    position: absolute;
    margin: auto;
    transform: rotate(45deg);
}

/* close button left side of X  */
#bx-{{ref}} .bx__btn-close:before {
    background: transparent;
    content: "";
    height: 20px;
    border-left: 2px solid [[ X Color ]];
    margin: auto;
    position: absolute;
    transform: rotate(-45deg);
}


/* mobile Styling */
@media only screen and (max-width: 600px) {
    /* banner */
  #bx-{{ref}} #bx_TopBanner .bx_TopBanner__banner {
    height: 100%;
    justify-content: space-around;
    padding: 20px 0;
    max-width: 99%;
  }

  /* text */
  #bx-{{ref}} #bx_TopBanner .bx_TopBanner__p--span {
    padding-left: 10px;
    line-height: 1.15;
    margin-bottom: 6px;
  }

  /* text container */
  #bx-{{ref}} #bx_TopBanner .bx_TopBanner__p {
    flex-direction: column;
    align-items: center;
    height: 100%;
    text-align: left;
  }
  
  /* banner container */
  #bx-{{ref}} #bx_TopBanner {
    height: 110px;
  }
  
  #bx-{{ref}} body.show-TopBanner {
    margin-top: 110px !important;
  }
  /* close btn */
  #bx-{{ref}} .bx__btn-close {
      top: 10px;
  }
}
```

### Javascript
```js
// Adds a unique variant identifier to CSS when deployed to ensure CSS does not impact styling of other elements.
var compiledCSS = Boxever.templating.compile(variant.assets.css)(variant);
var styleTag = document.getElementById('style-' + variant.ref);
if (styleTag) {
    styleTag.innerHTML = compiledCSS;
}
// End Adds a unique variant identifier to CSS when deployed to ensure CSS does not impact styling of other elements.

// make space in the body for the experience
document.body.classList.add("show-TopBanner");
insertHTMLBefore("body");


// Declarations
const bxButton = document.querySelector("#bx-"+variant.ref+ ' #bx_TopBanner-button');
const bxCloseButton = document.querySelector("#bx-"+variant.ref+ ' .bx__btn-close');
const bxExperience = document.querySelector("#bx-"+variant.ref+ ' #bx_TopBanner');

// Declare BX function event
const sendInteractionToBoxever = function(interactionType){
    let eventToSend = {
        "channel": "WEB",
        "type": "[[ Experience ID | String | ALERT_BAR | {required: true}]]_" + interactionType,
        "pos": window._boxever_settings.pointOfSale,
        "browser_id": Boxever.getID()
    };
    Boxever.eventCreate(eventToSend, function(data){ }, 'json');
}

//Listen on X button
bxCloseButton.addEventListener("click", function(){
    bxExperience.style.display = "none";
    document.body.classList.remove("show-TopBanner");
    sendInteractionToBoxever("DISMISSED")
});

// Listen on CTA button
bxButton.onclick = function(){
    sendInteractionToBoxever("CLICKED")
    location.href = "[[Button Link]]";
};
 
```
