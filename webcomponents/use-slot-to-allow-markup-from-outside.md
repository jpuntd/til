# use slot to allow markup from inside in your custom element

// rating.js
const template = document.createElement('template');
template.innerHTML = `

<style>
 // ...
</style>
<p>Rating</p>
<div class="rating-stars">
    <slot>
        <div class="rating-star"></div>
    </slot>
</div>
`;

Now we can use
