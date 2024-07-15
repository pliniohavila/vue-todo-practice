<template>
    <div class="card text-dark bg-info mb-3" style="max-width: 18rem;">
        <div class="card-header">
            <slot name="header">
                Header
            </slot>
        </div>
    <div class="card-body">
        <h5 class="card-title">
            <slot name="info">Info</slot>
        </h5>
        <p class="card-text">
            <slot name="body">
                Some quick example text to build on the card title and make up the bulk of the card's content.
            </slot>
        </p>
    </div>
</div>
</template>