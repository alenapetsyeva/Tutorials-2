---
title: Add a map display to your app
description: Add a map to your app and geolocate a street address
tags: [  tutorial>beginner, topic>sapui5, products>sap-hana-cloud-platform, products>sap-web-ide ]
---

## Prerequisites  
 - [Add an XML fragment for a tab in your app]

## Next Steps
 - [Translate your app into multiple languages]

## Details
### You will learn  
You will add a map display to one of the tabs in your app and geolocate an address associated with the item selected in the master (or list) view.
![Sample of the map from the Google Static Maps API Call](map-final-output.png)

### Time to Complete
**10 Min**.

---
[ACCORDION-BEGIN [STEP 1](Read about Google Static Maps API)]
1. You will be using the Google Static Maps API. For more information on this API, visit the [API Documentation Page](https://developers.google.com/maps/documentation/static-maps/intro).

    The Static Maps API returns an image that you can display in a HTML image tag.   

[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [STEP 2](Update the Map Fragment view)]
2. You will need an `Image` element in your view to hold the image graphic returned from the Google API. You will add it to the Map `Fragment` file (which is displayed when you click on the Map tab). You will add the code to the `SimpleForm` created in the previous step. The new code should be placed after the last form element, as indicated by the red arrow.

    ![Image of where to place new code for the view](xml-view-where-to-add-code.png)

    In `Map.fragment.xml`, add the following code after the last  `<Text>` element.  Then click **Save**.

    ```xml
    <core:Title text=" "/>
    <Image src="{
      parts: [
        'Address/Building'
        'Address/Street',
        'Address/PostalCode',
        'Address/City'
      ],
      formatter: '.formatter.formatMapUrl'
    }"  />
    ```

    You need to bind multiple attributes using `parts:` to get the full address. The address is composed of the Street Number, the Street Name, the Postal Code, and the City. The `formatter:` call will transform these parts into the proper form for the API call.

    The `<core:Title>` element will add a responsive 2nd column. On larger formats, like a desktop or iPad, you will see 2 columns. On smaller screens, like phones, you will see 1 column.

    Your final code should look like the screenshot below.

    ![image of final code for XML fragment](xml-view-final-code.png)
[VALIDATE 1]
[ACCORDION-END]

[ACCORDION-BEGIN [STEP 3](Update the Formatter JavaScript)]
3. You need to update your model `formatter.js` to include a new function call for the Google Static Maps API. In the `model` folder, open your `formatter.js` file. You will be adding a new function to the return of this function.

    ![Image of where to place new code for the js model](js-model-where-to-add-code.png)

    After you add the code, **Save** your changes.

    ```javascript
    /**
      * Formats an address to a static google maps image
      * @public
      * @param {string} sBuilding the building number
      * @param {string} sStreet the street
      * @param {string} sZIP the postal code
      * @param {string} sCity the city
      * @returns {string} sValue a google maps URL that can be bound to an image
      */
    formatMapUrl: function(sBuilding, sStreet, sZIP, sCity) {
      return "https://maps.googleapis.com/maps/api/staticmap?zoom=16&size=400x400&markers="
        + jQuery.sap.encodeURL(sBuilding +" "+ sStreet + ", " + sZIP +  " " + sCity );
    }
    ```

    Your function takes in the different parameters required to create an address. You return a text string of the Google API web address, which will return an image. You need to encode the text to a web-readable format by using the `jQuery.sap.encodeURL()` function. You can invoke this model formatter by using the `formatter` in the view.

    Your final code should look like the screenshot below.

    ![image of final code for Formatter js model ](js-model-final-code.png)
[VALIDATE 2]
[ACCORDION-END]

[ACCORDION-BEGIN [STEP 4](Run your application)]
4. Run your app. When you click on an item for more details, your page should look like the image below.

    ![Sample of the map from the Google Static Maps API Call](map-output.png)
[DONE]
[ACCORDION-END]

### Optional
Follow the below steps to make your map more unique.

[ACCORDION-BEGIN [STEP 5](Read about Styled Google Maps API)]
1. You can modify the URL created in the `formatter.js` to change features in the outputted map image. You can modify the URL to include a new `style`. You can modify the `style` by indicating the `feature` to update, the `element` within the feature to modify, and the `color` to change the element to. For more information on styling the map with Google, visit their [Styled Maps API Documentation](https://developers.google.com/maps/documentation/static-maps/styling).
[DONE]
[ACCORDION-END]

[ACCORDION-BEGIN [STEP 6](Add color to your map)]
2. Go to your `formatter.js` file, and modify the URL to include the new style. Feel free to try different colors. The [W 3 Schools color picker](http://www.w3schools.com/colors/colors_picker.asp) will provide you will the hexadecimal values for different colors. Don't forget to **Save** your changes before re-running your app.

    ```javascript
    return "https://maps.googleapis.com/maps/api/staticmap?zoom=13&size=400x400&treasureMode=aye&markers="
      + jQuery.sap.encodeURL(sBuilding + " " + sStreet + ", " + sZIP +  " " + sCity)
      + "&style=feature:road.highway%7Celement:geometry%7Cvisibility:simplified%7Ccolor:0xc280e9"
      + "&style=feature:poi%7Celement:geometry%7Ccolor:0x0080ff";
    ```

    The `feature` indicates that you want to update the highways. The `element` indicates that you want to change the styling of the geometry on the highways. And the `color` indicates which color the geometry of the highways should display as.
[DONE]
[ACCORDION-END]

## Next Steps
 - [Translate your app into multiple languages]
