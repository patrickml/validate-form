#validate-form

Basic bare bones form validation. Uses data attrs on the input to determine the validation to automatically apply. 
`onblur` attributes will be validated whenever the user blurs out of the input.



## Setup

`mrt add validate-form`

Validate-Form will bubble events up to the `layout` template by default. If your topmost template isn't named
that, configure it with the rootLayout flag. If you need to debug, add the debug flag to dump logs to the console.

```
// client.js

ValidateForm.config({
  debug: true
  rootLayout: 'myLayout'
});
```

## Useage

The simpleest setup is to add a form with an input. Using the `data-required` attr will
validate that it has at least one char. The `data-onblur` will make the input validate every
time the input is blurred.

```
<form id='new-user-form'>

  <input type="text" name="fullname" data-onblur data-required>
  <input type="submit"  value="Submit">
  
</form>             

```


```
Template.newUser.events({

  'submit form': function(e) {
    e.preventDefault();
    
    var isValid = ValidateForm.validate('#new-user-form');
    if (!isValid) return;
    
    .....
  }
})    

```