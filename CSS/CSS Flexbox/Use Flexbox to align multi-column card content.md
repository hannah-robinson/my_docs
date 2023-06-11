<< [[_Flexbox_]]

``` HTML
<div class="cards-wrapper">
  <div class="card">
    <div class="card__content">
      <h1>Card Heading</h1>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Ut nostrum voluptatibus dignissimos est veniam possimus, aperiam magnam earum modi officiis quae ipsa esse saepe neque voluptatum architecto? Ipsum, temporibus officiis.</p>
    </div>
    <div class="card__footer">
      <button>ADD TO CART</button>
    </div>
  </div>
</div>
```

``` CSS
.cards-wrapper {
    display: flex;
}

.card {
    flex: 25%;
    margin: 10px;
    border: 3px solid pink;
    display: flex;
    flex-direction: column;
}

.card__content {
    flex-grow: 1;
    flex-shrink: 1;
}

.card__footer {
    background-color: #BEBEBE;
    padding: 15px;
}
```