
# Vue Router Navigation Guard Alternate

This is not a big deal but I've developed a logic using Vue's watch functionality that accomplishes tasks similar to Vue Router's Navigation Guards. Typically, in Navigation Guards like router.beforeEach(), we handle tasks before Vue redirects to the next lifecycle point, such as verifying if the user is logged in or has permission to access a certain route. However, I encountered a limitation where certain details, like current route information, are unavailable within this guard. To address this, I've implemented separate logic using Vue's watch functionality. By doing so, I can dynamically monitor changes to specific data properties or state within my Vue components (in this case slug ```group_url``` get change). This approach allows me to perform actions similar to Navigation Guards while having access to necessary data within the Vue component's context. so in the example file ```Wrapper.vue``` when ```group_url``` get changed, the necessary details will be fetched and stored in ```vuex``` and redirect user based on the data.

Please note, in ```Wrapper.vue``` just added JS code


## Support

For support, email ronaksolanki1310@gmail.com
