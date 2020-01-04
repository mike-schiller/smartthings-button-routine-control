# SmartThings Button Routine Controller

This is a simple SmartThings Classic Application written for the hosted Groovy environment to allow the user to cycle
through a set of Routines by pushing, holding, or double pushing one or more compatible buttons. This
primarily targets the [Samsung SmartThings Button](https://www.samsung.com/us/smart-home/smartthings/buttons/samsung-smartthings-button-gp-u999sjvleaa/)
but will work with other buttons all that is strictly required is a button that implements the `pushed` event value.

The `double` and `held` event values have special meaning. The `double` event sets the application state to a starting
value, typically an off state. The `held` event sets the application to the last state, typically an all-on or
maximum setting.

The application setup allows the user to select which buttons control the state of the application as well as which
Routines are used by the application and map those Routines to the sequence of states controlled by the button
presses.

# Typical Usage

A typical use case for this application is to control the lighting in a room with multiple lights. A user would
create Scenes within SmartThings that specify the lighting levels. For example, an `off` Scene, a `low` Scene,
a `medium` Scene, and a `high` Scene. Because of the limitations of the SmartThings Classic API, Scenes are not
directly controllable, and the user must create a proxy Routine, likely with the same name, for each Scene.

In the application, the user would select one or more buttons to control the application, select the Routines to
be included, and then map the selected Routines to the desired order. For example, `off` => `low` => `medium` =>
`high`.

Assuming an initial state of `off`, single button presses would progress: `off` => `low` => `medium` => `high` =>
`off` => `low` ... and so on.

At any point, a double press would set the system to the `off` Routine and a long press would set the system to the
`high` Routine.

# Status
This applicatin is a work in progress, improvements are needed to the icons, error handling if no Routines are
available, and proper management of savability  during configuration in both intial configuration and reconfiguration.
Additionally, there is currently no provision for detecting state changes due to events other than the pressing of
the buttons configured for this application. In fact, it is likely impractical to handle that within this application.
