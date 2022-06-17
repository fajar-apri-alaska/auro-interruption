# Drawer

The `auro-drawer` is an intrusive interactive components, not passive. The component is best used when there is a requirement the user be made aware of the content being shown, moving focus from the main content to the dialog content.

The component also supports a modal (blocking) state where the user must interact with the content of the component in order to continue. Passive dismissal of the content is not allowed. Users of this state must add a trigger for the user to move beyond this content.

Auro holds the opinions of the [Nielsen Norman Group](https://www.nngroup.com/articles/modal-nonmodal-dialog/) on dialog and modal use to be true.

## Component use cases

The `auro-drawer` component should be used in situations where users may:

* Be prompted to take an action before doing anything else or going back
* Be prompted to view content with the option of closing it

## The setup

Triggering the drawer relies on functions being installed. See the following example code that is installed into this demo.

```javascript
toggleInterruption = (elName) => {
  let interruption = document.querySelector(elName);
  const html = document.querySelector('html');

  interruption.hasAttribute('open')
  ? interruption.removeAttribute("open")
  : (interruption.removeAttribute("open"),
    interruption.setAttribute("open", true))
}

// This function can be retrieved from https://unpkg.com/@alaskaairux/auro-interruption@latest/dist/toggleInterruption.js
```

Once the JavaScript is added to the scope of the experience, the next part is adding a trigger. In this example, the button component will toggle a dialog with the ID of `#demo1`.

``` html
<auro-button onClick="toggleInterruption('#demo1')">Open Dialog</auro-button>
```

## The structure

The structure of the dialog itself consists of three slots. The `header`, `content` and `footer` slots. See the scaffolding example below for adding content to the component.

``` html
  <auro-drawer id="[unique ID]">
    <span slot="header">[header content]</span>
    <span slot="content">
      [body content]
    </span>
    <span slot="footer">
      [footer content]
    </span>
  </auro-drawer>
```

It should be noted that the footer slot is reserved for the placement of action buttons.

## Drawer slide-in options (left, default)

The auro-drawer supports two different entry options. Using the `left` attribute, the component supports this slide-in mode for both mobile and desktop experiences.

<div class="demo--inline exampleWrapper auro_containedButtons">
  <auro-button onClick="toggleInterruption('#defaultDrawer')">Open default drawer</auro-button>
  <auro-button onClick="toggleInterruption('#leftDrawer')">Open left drawer</auro-button>

  <auro-drawer id="defaultDrawer">
    <span slot="header">Default Drawer</span>
    <div slot="content">
      <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">64alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
      <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
      <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
      <ul>
        <li>Caerphilly croque monsieur fondue</li>
        <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
        <li>Cheddar cheese and biscuits chalk and cheese</li>
        <li>Camembert de normandie stinking bishop bavarian bergkase</li>
      </ul>
    </div>
    <div slot="footer" class="auro_containedButtons">
      <auro-button secondary onClick="toggleInterruption('#defaultDrawer')">Close</auro-button>
    </div>
  </auro-drawer>

  <auro-drawer id="leftDrawer" left>
    <span slot="header">Left Drawer</span>
    <div slot="content">
      <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
      <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
      <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
      <ul>
        <li>Caerphilly croque monsieur fondue</li>
        <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
        <li>Cheddar cheese and biscuits chalk and cheese</li>
        <li>Camembert de normandie stinking bishop bavarian bergkase</li>
      </ul>
    </div>
    <div slot="footer" class="auro_containedButtons">
      <auro-button secondary onClick="toggleInterruption('#leftDrawer')">Close</auro-button>
    </div>
  </auro-drawer>
</div>

<auro-accordion lowProfile justifyRight>
  <span slot="trigger">See code</span>

```html
<auro-button onClick="toggleInterruption('#defaultDrawer')">Open default drawer</auro-button>
<auro-button onClick="toggleInterruption('#leftDrawer')">Open left drawer</auro-button>

<auro-drawer id="defaultDrawer">
  <span slot="header">Default Drawer</span>
  <div slot="content">
    <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
    <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
    <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
    <ul>
      <li>Caerphilly croque monsieur fondue</li>
      <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
      <li>Cheddar cheese and biscuits chalk and cheese</li>
      <li>Camembert de normandie stinking bishop bavarian bergkase</li>
    </ul>
  </div>
  <div slot="footer" class="auro_containedButtons">
    <auro-button secondary onClick="toggleInterruption('#defaultDialog')">Close</auro-button>
  </div>
</auro-drawer>

<auro-drawer id="leftDrawer" left>
  <span slot="header">Left Drawer</span>
  <div slot="content">
    <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
    <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
    <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
    <ul>
      <li>Caerphilly croque monsieur fondue</li>
      <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
      <li>Cheddar cheese and biscuits chalk and cheese</li>
      <li>Camembert de normandie stinking bishop bavarian bergkase</li>
    </ul>
  </div>
  <div slot="footer" class="auro_containedButtons">
    <auro-button secondary onClick="toggleInterruption('#defaultDialog')">Close</auro-button>
  </div>
</auro-drawer>
```

</auro-accordion>

## Drawer size options (sm, md)

The auro-drawer supports three different sizes. A default drawer is equal to the large size drawer. Using the `sm` and `md` attributes, the component supports these sizes for both mobile and desktop.

The size attribute effects the `width` of the desktop drawer. Its `height` is always 100%. On mobile, the `size` attribute effects the `maximum width` the drawer will use of the device screen.

<div class="demo--inline exampleWrapper auro_containedButtons">
  <auro-button onClick="toggleInterruption('#defaultDrawer')">Open default drawer</auro-button>
  <auro-button onClick="toggleInterruption('#mediumDrawer')">Open medium drawer</auro-button>
  <auro-button onClick="toggleInterruption('#smallDrawer')">Open small drawer</auro-button>
</div>

<auro-drawer id="defaultDrawer">
  <span slot="header">Default Drawer</span>
  <div slot="content">
    <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
    <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
    <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
    <ul>
      <li>Caerphilly croque monsieur fondue</li>
      <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
      <li>Cheddar cheese and biscuits chalk and cheese</li>
      <li>Camembert de normandie stinking bishop bavarian bergkase</li>
    </ul>
  </div>
  <div slot="footer" class="auro_containedButtons">
    <auro-button secondary onClick="toggleInterruption('#defaultDrawer')">Close</auro-button>
  </div>
</auro-drawer>

<auro-drawer id="mediumDrawer" md>
  <span slot="header">Medium Drawer</span>
  <div slot="content">
    <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
    <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
    <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
    <ul>
      <li>Caerphilly croque monsieur fondue</li>
      <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
      <li>Cheddar cheese and biscuits chalk and cheese</li>
      <li>Camembert de normandie stinking bishop bavarian bergkase</li>
    </ul>
  </div>
  <div slot="footer" class="auro_containedButtons">
    <auro-button secondary onClick="toggleInterruption('#mediumDrawer')">Close</auro-button>
  </div>
</auro-drawer>

<auro-drawer id="smallDrawer" sm>
  <span slot="header">Small Drawer</span>
  <div slot="content">
    <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
    <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
    <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
    <ul>
      <li>Caerphilly croque monsieur fondue</li>
      <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
      <li>Cheddar cheese and biscuits chalk and cheese</li>
      <li>Camembert de normandie stinking bishop bavarian bergkase</li>
    </ul>
  </div>
  <div slot="footer" class="auro_containedButtons">
    <auro-button secondary onClick="toggleInterruption('#smallDrawer')">Close</auro-button>
  </div>
</auro-drawer>

<auro-accordion lowProfile justifyRight>
  <span slot="trigger">See code</span>

  ```html
<auro-button onClick="toggleInterruption('#defaultDrawer')">Open default drawer</auro-button>
<auro-button onClick="toggleInterruption('#mediumDrawer')">Open medium drawer</auro-button>
<auro-button onClick="toggleInterruption('#smallDrawer')">Open small drawer</auro-button>

<auro-drawer id="defaultDrawer">
  <span slot="header">Default Drawer</span>
  <div slot="content">
    <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
    <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
    <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
    <ul>
      <li>Caerphilly croque monsieur fondue</li>
      <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
      <li>Cheddar cheese and biscuits chalk and cheese</li>
      <li>Camembert de normandie stinking bishop bavarian bergkase</li>
    </ul>
  </div>
  <div slot="footer" class="auro_containedButtons">
    <auro-button secondary onClick="toggleInterruption('#defaultDrawer')">Close</auro-button>
  </div>
</auro-drawer>

<auro-drawer id="mediumDrawer" md>
  <span slot="header">Medium Drawer</span>
  <div slot="content">
    <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
    <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
    <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
    <ul>
      <li>Caerphilly croque monsieur fondue</li>
      <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
      <li>Cheddar cheese and biscuits chalk and cheese</li>
      <li>Camembert de normandie stinking bishop bavarian bergkase</li>
    </ul>
  </div>
  <div slot="footer" class="auro_containedButtons">
    <auro-button secondary onClick="toggleInterruption('#mediumDrawer')">Close</auro-button>
  </div>
</auro-drawer>

<auro-drawer id="smallDrawer" sm>
  <span slot="header">Small Drawer</span>
  <div slot="content">
    <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
    <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
    <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
    <ul>
      <li>Caerphilly croque monsieur fondue</li>
      <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
      <li>Cheddar cheese and biscuits chalk and cheese</li>
      <li>Camembert de normandie stinking bishop bavarian bergkase</li>
    </ul>
  </div>
  <div slot="footer" class="auro_containedButtons">
    <auro-button secondary onClick="toggleInterruption('#smallDrawer')">Close</auro-button>
  </div>
</auro-drawer>
  ```

</auro-accordion>

## Modal Drawer and size options (sm, md, default)

The auro-drawer supports a modal drawer state that will lock a user into interacting with the `modal` drawer. To activate, use the modal attribute.

When using this state, the modal drawer must include a button action to dismiss the modal dialog as the closing icon will not be available and the user will not be able to click outside the modal drawer to dismiss.

<div class="demo--inline exampleWrapper auro_containedButtons">
  <auro-button onClick="toggleInterruption('#defaultModalDrawer')">Open default modal</auro-button>
  <auro-button onClick="toggleInterruption('#mediumModalDrawer')">Open medium modal</auro-button>
  <auro-button onClick="toggleInterruption('#smallModalDrawer')">Open small modal</auro-button>
</div>

<auro-drawer id="defaultModalDrawer" modal>
  <span slot="header">Default Modal Drawer</span>
  <div slot="content">
    <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
    <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
    <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
    <ul>
      <li>Caerphilly croque monsieur fondue</li>
      <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
      <li>Cheddar cheese and biscuits chalk and cheese</li>
      <li>Camembert de normandie stinking bishop bavarian bergkase</li>
    </ul>
  </div>
  <div slot="footer" class="auro_containedButtons">
    <auro-button onClick="toggleInterruption('#defaultModalDrawer')">I understand
      <auro-icon category="interface" name="chevron-right" emphasis onDark></auro-icon>
    </auro-button>
  </div>
</auro-drawer>

<auro-drawer id="mediumModalDrawer" md modal>
  <span slot="header">Medium Drawer</span>
  <div slot="content">
    <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
    <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
    <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
    <ul>
      <li>Caerphilly croque monsieur fondue</li>
      <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
      <li>Cheddar cheese and biscuits chalk and cheese</li>
      <li>Camembert de normandie stinking bishop bavarian bergkase</li>
    </ul>
  </div>
  <div slot="footer" class="auro_containedButtons">
    <auro-button onClick="toggleInterruption('#mediumModalDrawer')">I understand
      <auro-icon category="interface" name="chevron-right" emphasis onDark></auro-icon>
    </auro-button>
  </div>
</auro-drawer>

<auro-drawer id="smallModalDrawer" sm modal>
  <span slot="header">Small Drawer</span>
  <div slot="content">
    <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
    <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
    <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
    <ul>
      <li>Caerphilly croque monsieur fondue</li>
      <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
      <li>Cheddar cheese and biscuits chalk and cheese</li>
      <li>Camembert de normandie stinking bishop bavarian bergkase</li>
    </ul>
  </div>
  <div slot="footer" class="auro_containedButtons">
    <auro-button onClick="toggleInterruption('#smallModalDrawer')">I understand
      <auro-icon category="interface" name="chevron-right" emphasis onDark></auro-icon>
    </auro-button>
  </div>
</auro-drawer>

<auro-accordion lowProfile justifyRight>
  <span slot="trigger">See code</span>

  ```html
<auro-button onClick="toggleInterruption('#defaultModalDrawer')">Open default modal</auro-button>
<auro-button onClick="toggleInterruption('#mediumModalDrawer')">Open medium modal</auro-button>
<auro-button onClick="toggleInterruption('#smallModalDrawer')">Open small modal</auro-button>

<auro-drawer id="defaultModalDrawer" modal>
  <span slot="header">Default Modal Drawer</span>
  <div slot="content">
    <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
    <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
    <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
    <ul>
      <li>Caerphilly croque monsieur fondue</li>
      <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
      <li>Cheddar cheese and biscuits chalk and cheese</li>
      <li>Camembert de normandie stinking bishop bavarian bergkase</li>
    </ul>
  </div>
  <div slot="footer" class="auro_containedButtons">
    <auro-button onClick="toggleInterruption('#defaultModalDrawer')">I understand
      <auro-icon category="interface" name="chevron-right" emphasis onDark></auro-icon>
    </auro-button>
  </div>
</auro-drawer>

<auro-drawer id="mediumModalDrawer" md modal>
  <span slot="header">Medium Drawer</span>
  <div slot="content">
    <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
    <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
    <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
    <ul>
      <li>Caerphilly croque monsieur fondue</li>
      <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
      <li>Cheddar cheese and biscuits chalk and cheese</li>
      <li>Camembert de normandie stinking bishop bavarian bergkase</li>
    </ul>
  </div>
  <div slot="footer" class="auro_containedButtons">
    <auro-button onClick="toggleInterruption('#mediumModalDrawer')">I understand
      <auro-icon category="interface" name="chevron-right" emphasis onDark></auro-icon>
    </auro-button>
  </div>
</auro-drawer>

<auro-drawer id="smallModalDrawer" sm modal>
  <span slot="header">Small Drawer</span>
  <div slot="content">
    <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
    <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
    <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
    <ul>
      <li>Caerphilly croque monsieur fondue</li>
      <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
      <li>Cheddar cheese and biscuits chalk and cheese</li>
      <li>Camembert de normandie stinking bishop bavarian bergkase</li>
    </ul>
  </div>
  <div slot="footer" class="auro_containedButtons">
    <auro-button onClick="toggleInterruption('#smallModalDrawer')">I understand
      <auro-icon category="interface" name="chevron-right" emphasis onDark></auro-icon>
    </auro-button>
  </div>
</auro-drawer>
  ```

</auro-accordion>

## Drawer with decoupled experiences

For use case where the size of the drawer on desktop should not influence the size of the drawer on mobile, the combination API of `sm lg` and `md lg` can be used.

The use of these combinations will set the first value to the drawer for a desktop experience. The second value will set the mobile experience to be up to 90% of the screen.

See the following examples.

<div class="demo--inline exampleWrapper auro_containedButtons">
  <auro-button onClick="toggleInterruption('#smLgDrawer')">Open [sm lg] drawer</auro-button>
  <auro-button onClick="toggleInterruption('#smMdDrawer')">Open [md lg] drawer</auro-button>
</div>

<auro-drawer id="smLgDrawer" sm lg>
  <span slot="header">Small Modal Drawer</span>
  <div slot="content">
    <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
    <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
    <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
    <ul>
      <li>Caerphilly croque monsieur fondue</li>
      <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
      <li>Cheddar cheese and biscuits chalk and cheese</li>
      <li>Camembert de normandie stinking bishop bavarian bergkase</li>
    </ul>
  </div>
  <div slot="footer" class="auro_containedButtons">
    <auro-button onClick="toggleInterruption('#smLgDrawer')">I understand
      <auro-icon category="interface" name="check-lg" emphasis onDark></auro-icon>
    </auro-button>
  </div>
</auro-drawer>

<auro-drawer id="smMdDrawer" md lg>
  <span slot="header">Medium Modal Drawer</span>
  <div slot="content">
    <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
    <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
    <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
    <ul>
      <li>Caerphilly croque monsieur fondue</li>
      <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
      <li>Cheddar cheese and biscuits chalk and cheese</li>
      <li>Camembert de normandie stinking bishop bavarian bergkase</li>
    </ul>
  </div>
  <div slot="footer" class="auro_containedButtons">
    <auro-button onClick="toggleInterruption('#smMdDrawer')">I understand
      <auro-icon category="interface" name="check-lg" emphasis onDark></auro-icon>
    </auro-button>
  </div>
</auro-drawer>

<auro-accordion lowProfile justifyRight>
  <span slot="trigger">See code</span>

  ```html
<auro-button onClick="toggleInterruption('#smLgDrawer')">Open [sm lg] drawer</auro-button>
<auro-button onClick="toggleInterruption('#smMdDrawer')">Open [md lg] drawer</auro-button>

<auro-drawer id="smLgDrawer" sm lg>
  <span slot="header">Small Modal Drawer</span>
  <div slot="content">
    <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
    <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
    <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
    <ul>
      <li>Caerphilly croque monsieur fondue</li>
      <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
      <li>Cheddar cheese and biscuits chalk and cheese</li>
      <li>Camembert de normandie stinking bishop bavarian bergkase</li>
    </ul>
  </div>
  <div slot="footer" class="auro_containedButtons">
    <auro-button onClick="toggleInterruption('#smLgDrawer')">I understand
      <auro-icon category="interface" name="check-lg" emphasis onDark></auro-icon>
    </auro-button>
  </div>
</auro-drawer>

<auro-drawer id="smMdDrawer" md lg>
  <span slot="header">Medium Modal Drawer</span>
  <div slot="content">
    <p>When traveling on Alaska Airlines flights, Alaska Airlines checked baggage fees may apply. See <auro-hyperlink href="https://www.alaskaair.com/bagrules" target="_blank">alaskaair.com/bagrules</auro-hyperlink> for our rules. For itineraries that include other airlines, their checked baggage fees may apply, as displayed on their websites.</p>
    <p>Baggage rules and fees will be based on the specific itinerary chosen. The applicable first and second bag fees will be displayed after you have added flights to the cart.</p>
    <auro-header level="3" display="500">Before checking your bags, remember to:</auro-header>
    <ul>
      <li>Caerphilly croque monsieur fondue</li>
      <li>Taleggio goat mascarpone cow manchego cheese and wine emmental cheese strings</li>
      <li>Cheddar cheese and biscuits chalk and cheese</li>
      <li>Camembert de normandie stinking bishop bavarian bergkase</li>
    </ul>
  </div>
  <div slot="footer" class="auro_containedButtons">
    <auro-button onClick="toggleInterruption('#smMdDrawer')">I understand
      <auro-icon category="interface" name="check-lg" emphasis onDark></auro-icon>
    </auro-button>
  </div>
</auro-drawer>
  ```

</auro-accordion>

## Unformatted drawer

For use case where the use of a drawer is to be more freeform, but the experience and base tooling for the drawer are still requested, there is the `unformatted` property.

This property can be used in combination of any other use case of the drawer, but it will render a unformatted drawer window allowing for full customization of content within the scope of the window.

### Responsive padding

Part of the drawer design spec is its responsive padding. To take advantage of this for your content within the scope of the drawer, be sure to use the selector `unformattedWrapper` that can be imported from the package here;

```scss
import '@alaskaairux/auro-interruption/dist/style-unformatted.scss'

or

import '@alaskaairux/auro-interruption@/dist/style-unformatted.css'
```

### Accessibility

Within the scope of the auro-drawer there is `aria-labelledby="dialog-header"`. To make proper use of this, in an unformatted drawer, the developer is required to add `id="dialog-header"` to the content header within the drawer content.

<div class="demo--inline exampleWrapper auro_containedButtons">
  <auro-button onClick="toggleInterruption('#unformattedMdDrawer')">Unformatted Medium Dialog</auro-button>
</div>

<link rel="stylesheet" href="https://unpkg.com/@alaskaairux/auro-interruption@latest/dist/style-unformatted.css" />

<auro-drawer id="unformattedMdDrawer" unformatted md lg ondark>
  <span slot="content">
    <img style="display: block; width: 100%" src="https://blog.alaskaair.com/wp-content/uploads/2020/11/111-psp-blog-img-guide.jpg" alt="alaska airlines pride lights" />
    <div class="unformattedWrapper">
      <h1 id="dialog-header">This is a header</h1>
      These are words that are slotted into the scope of the custom element.
    </div>
  </span>
</auro-drawer>

<auro-accordion lowProfile justifyRight>
  <span slot="trigger">See code</span>

```html
<link rel="stylesheet" href="https://unpkg.com/@alaskaairux/auro-interruption@latest/dist/style-unformatted.css">

<auro-button onClick="toggleInterruption('#unformattedMdDialog')">Unformatted Medium Dialog</auro-button>

<auro-drawer id="unformattedMdDrawer" unformatted md lg ondark>
  <span slot="content">
    <img style="display: block; width: 100%" src="https://blog.alaskaair.com/wp-content/uploads/2020/11/111-psp-blog-img-guide.jpg" alt="alaska airlines pride lights" />
    <div class="unformattedWrapper">
      <h1 id="dialog-header">This is a header</h1>
      These are words that are slotted into the scope of the custom element.
    </div>
  </span>
</auro-drawer>
```
</auro-accordion>

### Edit close button position

When using the drawer with the `unformatted` attribute, some may want to adjust the positioning of the X close button. This can be addressed using the CSS `::part` CSS pseudo-element API.

<div class="demo--inline exampleWrapper auro_containedButtons">
  <auro-button onClick="toggleInterruption('#unformattedCustomMdDrawer')">Unformatted w/custom close button</auro-button>
</div>

<link rel="stylesheet" href="https://unpkg.com/@alaskaairux/auro-interruption@latest/dist/style-unformatted.css" />

<style>
  .example::part(close-button) {
    top: var(--auro-size-xl);
    right: var(--auro-size-xl);
    color: var(--auro-color-brand-flamingo-500);
  }
</style>

<auro-drawer id="unformattedCustomMdDrawer" unformatted md lg class="example">
  <span slot="content">
    <img style="display: block; width: 100%" src="https://worldairlinenews.files.wordpress.com/2022/05/alaska-737-800-sswl-n538as-22-star-warstko-sfo-mdblr-5.4.22.jpg" alt="alaska airlines pride lights" />
    <div class="unformattedWrapper">
      <h1 id="dialog-header">Unformatted w/custom close button</h1>
      Notice the custom location of the close button as well as the custom color.
    </div>
  </span>
</auro-drawer>

<auro-accordion lowProfile justifyRight>
  <span slot="trigger">See code</span>

```html
<link rel="stylesheet" href="https://unpkg.com/@alaskaairux/auro-interruption@latest/dist/style-unformatted.css" />

<style>
  .example::part(close-button) {
    top: var(--auro-size-xl);
    right: var(--auro-size-xl);
    color: var(--auro-color-brand-flamingo-500);
  }
</style>

<auro-drawer id="unformattedCustomMdDrawer" unformatted md lg class="example">
  <span slot="content">
    <img style="display: block; width: 100%" src="https://worldairlinenews.files.wordpress.com/2022/05/alaska-737-800-sswl-n538as-22-star-warstko-sfo-mdblr-5.4.22.jpg" alt="alaska airlines pride lights" />
    <div class="unformattedWrapper">
      <h1 id="dialog-header">Unformatted w/custom close button</h1>
      Notice the custom location of the close button as well as the custom color.
    </div>
  </span>
</auro-drawer>
```
</auro-accordion>
