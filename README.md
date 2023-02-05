Do the usual:

- clone
- npm i
- npm run serve

Current Behaviour:

This starts with a simple form with two inputs.

1. hit the `Show Helper`
   1. helper text shows
   1. lighter in old style than new
   1. there is a line that appears under new
1. hit the `Show Error`
   1. error text shows
   1. click into the inputs
      1. old style shows red underline
      1. new style does not
1. hit the `Reset`
   1. messages are no longer shown
   1. line for the "new" style is still shown
