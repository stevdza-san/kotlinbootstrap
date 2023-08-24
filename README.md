<p align="center">
  <a href="#">
    <img src="/ASSETS/logo.svg" alt="Kotlin-Bootstrap logo" width="200" height="165">
  </a>
</p>

<h3 align="center">Kotlin Bootstrap</h3>
<p align="center">
  ⚡Highly experimental library built on top of the <a href="https://github.com/varabyte/kobweb" target="_blank" rel="noopener noreferrer">Kobweb</a>(Compose HTML framework). It allows you to use the official <a href="https://getbootstrap.com/" target="_blank" rel="noopener noreferrer">Bootstrap</a> UI components with Kotlin and Jetpack Compose, to build a frontend on the web. You are required to use the kobweb framework, otherwise it won't work.
</p>


## Available Components
- [Button](#button)
- [Input](#input)
- [Dropdown](#dropdown)
- [TextArea](#textarea)
- [Checkbox](#checkbox)
- [RadioButton](#radiobutton)
- [Switch](#switch)

## Usage
Update a Project level `build.gradle.kts` file:

```gradle
repositories {
    ..
    maven(url = "https://jitpack.io")
}
```

Update a `site` module `build.gradle.kts` file:

```gradle
kobweb {
    app {
        index {
            head.add {
                script {
                    src = "https://cdn.jsdelivr.net/npm/bootstrap@5.3.1/dist/js/bootstrap.bundle.min.js"
                }
                link {
                    rel = "stylesheet"
                    href = "https://cdn.jsdelivr.net/npm/bootstrap@5.3.1/dist/css/bootstrap.min.css"
                }
            }
        }
    }
}

kotlin {
    @Suppress("UNUSED_VARIABLE") 
    sourceSets {
        ..
        val jsMain by getting {
            dependencies {
                ..
                implementation("com.github.stevdza-san:KotlinBootstrap:0.0.1")
            }
        }
    }
}
```

## Button
<p>
  <img src="/ASSETS/buttons.png" alt="Buttons Preview" width="812">
</p> 

<p>
  <img src="/ASSETS/loadingButton.gif?raw=true" width="268"/>
  <img src="/ASSETS/loadingButtonText.gif?raw=true" width="268"/>
    <img src="/ASSETS/badgeButton.gif?raw=true" width="268"/>
</p>

<p>A simple button usage:</p>

```kotlin
BSButton(
    text = "Sign in",
    onClick = {}
)
```

<p>You can update your button state to loading, as well as specify the exact Loading Text <em>(optional)</em>:</p>

```kotlin
var buttonLoading by remember { mutableStateOf(false) }
BSButton(
    text = "Sign in",
    loading = buttonLoading,
    loadingText = "Please wait...",
    onClick = { buttonLoading = true }
)
```

<p>Add a Badge to your button:</p>

```kotlin
BSButton(
    text = "Shopping Cart",
    badge = ButtonBadge(
        text = "10"
    ),
    onClick = {}
)
```

## Input
<p>
  <img src="/ASSETS/inputs.gif" alt="Inputs Preview" width="360">
</p> 

<p>A simple usage with a placeholder:</p>

```kotlin
var inputValue by remember { mutableStateOf("") }
BSInput(
    value = inputValue,
    placeholder = "Type here",
    onValueChange = {
        inputValue = it
    }
)
```

<p>Floating style input field, where a label is animated:</p>

```kotlin
BSInput(
    value = inputValue,
    label = "Email Address",
    onValueChange = {},
    floating = true
)
```

<p>Positive validation style input field:</p>

```kotlin
BSInput(
    value = inputValue,
    label = "Email Address",
    placeholder = "Type here",
    onValueChange = {},
    validation = InputValidation(
      isValid = true
    )
)
```

<p>Negative validation style input field:</p>

```kotlin
BSInput(
    value = inputValue,
    label = "Email Address",
    placeholder = "Type here",
    onValueChange = {},
    validation = InputValidation(
      isInvalid = true
    )
)
```

<p>Disabled input field:</p>

```kotlin
BSInput(
    value = inputValue,
    label = "Email Address",
    placeholder = "Type here",
    onValueChange = {},
    disabled = true
)
```

<p>Plain text input field:</p>

```kotlin
BSInput(
    value = inputValue,
    label = "Email Address",
    placeholder = "Type here",
    plainText = true,
    onValueChange = {}
)
```

## Dropdown
<p>
  <img src="/ASSETS/dropdowns.png" alt="Dropdown Preview" width="812">
</p> 

<p>
  <img src="/ASSETS/placeholderDropdown.gif?raw=true" width="268"/>
  <img src="/ASSETS/darkBackgroundDropdown.gif?raw=true" width="268"/>
    <img src="/ASSETS/disabledDropdown.gif?raw=true" width="268"/>
</p>

<p>Dropdown with a placeholder:</p>

```kotlin
BSDropdown(
    placeholder = "Select a Platform",
    items = listOf("Android", "iOS", "Web"),
    onItemSelect = { index, value -> }
)
```

<p>Dropdown with a dark background:</p>

```kotlin
BSDropdown(
    items = listOf("Android", "iOS", "Web"),
    darkBackground = true,
    onItemSelect = { index, value -> }
)
```

<p>Disabled Dropdown item:</p>

```kotlin
BSDropdown(
    items = listOf("Android", "iOS", "Web"),
    disabledItems = listOf("iOS"),
    onItemSelect = { index, value -> }
)
```

## TextArea
<p>
  <img src="/ASSETS/textarea.gif?raw=true" alt="TextArea Preview" width="460">
</p> 


<p>Basic TextArea example with a label:</p>

```kotlin
var value by remember { mutableStateOf("") }
BSTextArea(
    value = value,
    label = "Email Address",
    placeholder = "Type here...",
    onValueChange = { value = it }
)
```

<p>Floating TextArea:</p>

```kotlin
var value by remember { mutableStateOf("") }
BSTextArea(
    value = value,
    label = "Email Address",
    floating = true,
    onValueChange = { value = it }
)
```

## Checkbox
<p>
  <img src="/ASSETS/checkboxes.gif?raw=true" alt="Checkboxes Preview" width="280">
</p> 

<p>Basic Checkbox usage:</p>

```kotlin
BSCheckbox(
    label = "Kotlin",
    onClick = {}
)
```

<p>Reversed order checkbox:</p>

```kotlin
BSCheckbox(
    label = "C++",
    reverse = true,
    onClick = {}
)
```

<p>Toggle button style checkbox:</p>

```kotlin
BSCheckbox(
    label = "Python",
    toggleButton = true,
    onClick = {}
)
```

## RadioButton
<p>
  <img src="/ASSETS/radiobuttons.gif?raw=true" alt="RadioButtons Preview">
</p> 

<p>Basic RadioButtonGroup usage:</p>

```kotlin
BSRadioButtonGroup {
    BSRadioButton(label = "Android", onClick = {})
    BSRadioButton(label = "iOS", onClick = {})
    BSRadioButton(label = "Web", onClick = {})
}
```

<p>RadioButtonGroup in a horizontal orientation:</p>

```kotlin
BSRadioButtonGroup(inline = true) {
    BSRadioButton(label = "Android", onClick = {})
    BSRadioButton(label = "iOS", onClick = {})
    BSRadioButton(label = "Web", onClick = {})
}
```

<p>ToggleButton style of a RadioButtonGroup:</p>

```kotlin
BSRadioButtonGroup(toggleButton = true) {
    BSRadioButton(label = "Android", onClick = {})
    BSRadioButton(label = "iOS", onClick = {})
    BSRadioButton(label = "Web", onClick = {})
}
```

## Switch
<p>
  <img src="/ASSETS/switches.gif?raw=true" alt="Switches Preview" width="700">
</p> 

<p>Switch with a default checked state:</p>

```kotlin
BSSwitch(
    label = "Android",
    defaultChecked = true,
    onClick = {}
)
```

<p>Disabled Switch with a default unchecked state:</p>

```kotlin
BSSwitch(
    label = "Android",
    disabled = true,
    onClick = {}
)
```
