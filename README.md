Javascripty section
-------------------

Learning Objectives:
  * Understand how javascript interacts with the page, and introduce jquery

Explain what javascript is & the sort of things we can do with it in webpages

Show them the 'completed' example page and demonstrate the bits we've used jquery with (comments form & comments area).

Explain that we'll be building something similar on their pages using jquery

Tasks to talk them through:


   * Getting used to jquery. Add jquery cdn to page:

```
  <script src="https://code.jquery.com/jquery-2.2.0.min.js"></script>
```

* Add a simple button to the page somewhere and bind an onclick handler to the button to show an alert box:

```html
<button id="learn-more" class="btn btn-success btn-lg" type="button">Learn More</button>

...

<script>

$('#learn-more').click( function() {
    alert( 'Learn more about what?');
});

</script>

```

Demonstrates jquery selectors, and binding functions in response to events. Worth mentioning that there are other ways to select elements.

*  Start building the comments section. Explain that we'll be taking the form input (name & comment) & using jquery to add the
   comment to the bottom of the page in a comments block


   * Add div to hold comments:

```html
   <div class="col-md-8 col-md-offset-2">
      <h2>Comments</h2>
      <div id="comments">
      </div>
   </div>
```

   * Add a form for users to enter a comment:

```html
<div class="col-md-4 col-md-offset-4 form" style="margin-top:20px">
   <div class="form-group">
        <label for="name">Name</label>
        <input type="text" id="name" class="form-control" placeholder="name goes here" />
   </div>
   <div class="form-group">
        <label for="comment">Comment</label>
        <textarea type="text" id="comment" class="form-control" placeholder="comment goes here" maxlength="150" rows="5" cols="10"></textarea>
   </div>
   <div class="form-group">
        <button id="addComment" class="btn btn-success pull-right">Submit</button>
   </div>
</div>
```

   * Give them the function to add a comment to the page:

```html
function addComment(name, comment){
    var date = new Date();

    var html = '<div class="comment row">' +
       '<div class="commentator col-xs-7"> ' + name + ' says: </div>' +
       '<div class="col-xs-5 removeBox"><span class="remove">x</span></div>' +
       '<div class="col-xs-12 commentText">' + comment + '</div>' +
       '<div class="col-xs-12 commentDate">' + date.toLocaleDateString() + '</div>' +
    '</div>';

    $(html).hide().appendTo("#comments").fadeIn(400);
}
```

   * Add onclick handler to form button to grab name and comment text and call our function.

```html
<script>
$("#addComment").click(function(){
    var name = $("#name").val();
    var comment = $("#comment").val();
    addComment(name, comment);
});
</script>
```


   * Add a handler to remove the comments when a user clicks the remove button:

```html
<script>
$("#comments").on("click", ".remove", function(){
   removeComment($(this));
});

function removeComment($removeButton){
    var $commentBox = $removeButton.parents(".comment");
    $commentBox.fadeOut(400);
}
</script>
```

* Transforms/animations

BONUS:
jigger about with style using buttons/select box.
