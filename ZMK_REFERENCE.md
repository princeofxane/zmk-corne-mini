# 🎹 ZMK Firmware - Complete Reference Guide

> A comprehensive, beginner-friendly reference for ZMK firmware keybindings, behaviors, and configurations

[![ZMK](https://img.shields.io/badge/ZMK-Firmware-blue)](https://zmk.dev/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Corne](https://img.shields.io/badge/Keyboard-Corne-orange)](https://github.com/foostan/crkbd)

---

## 📋 Table of Contents

- [🎹 ZMK Firmware - Complete Reference Guide](#-zmk-firmware---complete-reference-guide)
  - [📋 Table of Contents](#-table-of-contents)
  - [🚀 Quick Start](#-quick-start)
  - [⚡ Basic Behaviors](#-basic-behaviors)
  - [⌨️ Key Codes](#️-key-codes)
    - [Letters](#letters)
    - [Numbers](#numbers)
    - [Function Keys](#function-keys)
    - [Modifiers](#modifiers)
    - [Special Keys](#special-keys)
    - [Navigation](#navigation)
    - [Symbols (Unshifted)](#symbols-unshifted)
    - [Symbols (Shifted)](#symbols-shifted)
    - [Media Keys](#media-keys)
    - [System Keys](#system-keys)
  - [🔄 Layer Management](#-layer-management)
  - [🎛️ Modifier Behaviors](#️-modifier-behaviors)
  - [📡 Bluetooth Controls](#-bluetooth-controls)
  - [🛠️ Custom Behaviors](#️-custom-behaviors)
  - [🎬 Macros](#-macros)
  - [🔗 Combos](#-combos)
  - [🔀 Conditional Layers](#-conditional-layers)
  - [📝 Your Current Setup Reference](#-your-current-setup-reference)
  - [💡 Common Patterns](#-common-patterns)
  - [✨ Tips \& Best Practices](#-tips--best-practices)
  - [🔗 Resources](#-resources)

---

## 🚀 Quick Start

**New to ZMK?** Start here:

1. **Basic key press**: `&kp A` - Press the 'A' key
2. **Transparent key**: `&trans` - Pass through to layer below
3. **Layer access**: `&mo 1` - Hold to activate layer 1
4. **Mod-tap**: `&mt LSHIFT SPACE` - Tap for space, hold for shift

**Key position numbering** (Corne layout):
```
Left Hand:                    Right Hand:
 0   1   2   3   4   5        6   7   8   9  10  11
12  13  14  15  16  17       18  19  20  21  22  23
24  25  26  27  28  29       30  31  32  33  34  35
            36  37  38       39  40  41
```

---

## ⚡ Basic Behaviors

These are the fundamental building blocks of your keymap.

### Core Behaviors

| Syntax | Name | Description | Use Case |
|--------|------|-------------|----------|
| `&kp` | **Key Press** | Standard key press | Most keys - letters, numbers, symbols |
| `&trans` | **Transparent** | Pass through to layer below | Reuse keys from base layer |
| `&none` | **None** | Do nothing, block lower layers | Disable a key completely |
| `&bootloader` | **Bootloader** | Enter bootloader mode | Flash new firmware |
| `&reset` | **Reset** | Software reset keyboard | Troubleshooting |
| `&studio_unlock` | **Studio Unlock** | Unlock ZMK Studio | Advanced configuration |

### 💡 Usage Examples

```c
// Basic key presses
&kp A           // Press the 'A' key
&kp SPACE       // Press spacebar
&kp LSHIFT      // Press left shift

// Layer management
&trans          // Transparent - use whatever key is on the layer below
&none           // Do nothing - this key is disabled

// System
&bootloader     // Enter bootloader mode to flash firmware
&reset          // Reset the keyboard
```

---

## ⌨️ Key Codes

Complete reference for all available key codes in ZMK.

<details>
<summary><b>📖 Click to expand full key code reference</b></summary>

### Letters
```c
&kp A, &kp B, &kp C, &kp D, &kp E, &kp F, &kp G, &kp H, &kp I, &kp J
&kp K, &kp L, &kp M, &kp N, &kp O, &kp P, &kp Q, &kp R, &kp S, &kp T
&kp U, &kp V, &kp W, &kp X, &kp Y, &kp Z
```

### Numbers
```c
// Top row numbers
&kp N0, &kp N1, &kp N2, &kp N3, &kp N4
&kp N5, &kp N6, &kp N7, &kp N8, &kp N9

// Keypad numbers
&kp KP_N0, &kp KP_N1, &kp KP_N2, &kp KP_N3, &kp KP_N4
&kp KP_N5, &kp KP_N6, &kp KP_N7, &kp KP_N8, &kp KP_N9
```

### Function Keys
```c
// F1-F12
&kp F1,  &kp F2,  &kp F3,  &kp F4,  &kp F5,  &kp F6
&kp F7,  &kp F8,  &kp F9,  &kp F10, &kp F11, &kp F12

// F13-F24 (rarely used, great for custom shortcuts!)
&kp F13, &kp F14, &kp F15, &kp F16, &kp F17, &kp F18
&kp F19, &kp F20, &kp F21, &kp F22, &kp F23, &kp F24
```

### Modifiers

| Key | Aliases | Description |
|-----|---------|-------------|
| `&kp LSHIFT` | `&kp LSHFT` | Left Shift |
| `&kp LCTRL` | `&kp LCTL` | Left Control |
| `&kp LALT` | - | Left Alt |
| `&kp LGUI` | `&kp LCMD`, `&kp LWIN` | Left GUI/Command/Windows |
| `&kp RSHIFT` | `&kp RSHFT` | Right Shift |
| `&kp RCTRL` | `&kp RCTL` | Right Control |
| `&kp RALT` | - | Right Alt |
| `&kp RGUI` | `&kp RCMD`, `&kp RWIN` | Right GUI/Command/Windows |

### Special Keys

| Key | Aliases | Output |
|-----|---------|--------|
| `&kp SPACE` | `&kp SPC` | Spacebar |
| `&kp TAB` | - | Tab |
| `&kp RET` | `&kp ENTER` | Enter/Return |
| `&kp ESC` | `&kp ESCAPE` | Escape |
| `&kp BSPC` | `&kp BACKSPACE` | Backspace |
| `&kp DEL` | `&kp DELETE` | Delete |
| `&kp CAPS` | `&kp CAPSLOCK` | Caps Lock |

### Navigation

| Key | Aliases | Description |
|-----|---------|-------------|
| `&kp LEFT` | `&kp LEFT_ARROW` | ← |
| `&kp RIGHT` | `&kp RIGHT_ARROW` | → |
| `&kp UP` | `&kp UP_ARROW` | ↑ |
| `&kp DOWN` | `&kp DOWN_ARROW` | ↓ |
| `&kp HOME` | - | Home |
| `&kp END` | - | End |
| `&kp PG_UP` | `&kp PAGE_UP` | Page Up |
| `&kp PG_DN` | `&kp PAGE_DOWN` | Page Down |

### Symbols (Unshifted)

| Key | Aliases | Output |
|-----|---------|--------|
| `&kp GRAVE` | `&kp TILDE` | `` ` `` |
| `&kp MINUS` | `&kp UNDER` | `-` |
| `&kp EQUAL` | `&kp PLUS` | `=` |
| `&kp LBKT` | `&kp LEFT_BRACKET` | `[` |
| `&kp RBKT` | `&kp RIGHT_BRACKET` | `]` |
| `&kp BSLH` | `&kp BACKSLASH` | `\` |
| `&kp SEMI` | `&kp SEMICOLON` | `;` |
| `&kp SQT` | `&kp SINGLE_QUOTE` | `'` |
| `&kp COMMA` | - | `,` |
| `&kp DOT` | `&kp PERIOD` | `.` |
| `&kp FSLH` | `&kp SLASH` | `/` |

### Symbols (Shifted)

| Key | Aliases | Output |
|-----|---------|--------|
| `&kp EXCL` | `&kp EXCLAMATION` | `!` |
| `&kp AT` | - | `@` |
| `&kp HASH` | `&kp POUND` | `#` |
| `&kp DLLR` | `&kp DOLLAR` | `$` |
| `&kp PRCNT` | `&kp PERCENT` | `%` |
| `&kp CARET` | - | `^` |
| `&kp AMPS` | `&kp AMPERSAND` | `&` |
| `&kp ASTRK` | `&kp ASTERISK`, `&kp STAR` | `*` |
| `&kp LPAR` | `&kp LEFT_PARENTHESIS` | `(` |
| `&kp RPAR` | `&kp RIGHT_PARENTHESIS` | `)` |
| `&kp UNDER` | `&kp UNDERSCORE` | `_` |
| `&kp PLUS` | - | `+` |
| `&kp LBRC` | `&kp LEFT_BRACE` | `{` |
| `&kp RBRC` | `&kp RIGHT_BRACE` | `}` |
| `&kp PIPE` | - | `\|` |
| `&kp COLON` | - | `:` |
| `&kp DQT` | `&kp DOUBLE_QUOTES` | `"` |
| `&kp LT` | `&kp LESS_THAN` | `<` |
| `&kp GT` | `&kp GREATER_THAN` | `>` |
| `&kp QMARK` | `&kp QUESTION` | `?` |

### Media Keys

| Key | Aliases | Description |
|-----|---------|-------------|
| `&kp C_PLAY_PAUSE` | `&kp C_PP` | Play/Pause ⏯️ |
| `&kp C_NEXT` | - | Next Track ⏭️ |
| `&kp C_PREV` | - | Previous Track ⏮️ |
| `&kp C_STOP` | - | Stop ⏹️ |
| `&kp C_VOL_UP` | - | Volume Up 🔊 |
| `&kp C_VOL_DN` | - | Volume Down 🔉 |
| `&kp C_MUTE` | - | Mute 🔇 |
| `&kp C_BRI_UP` | - | Brightness Up 🔆 |
| `&kp C_BRI_DN` | - | Brightness Down 🔅 |

### System Keys

| Key | Aliases | Description |
|-----|---------|-------------|
| `&kp K_COPY` | - | Copy (Ctrl+C) |
| `&kp K_PASTE` | - | Paste (Ctrl+V) |
| `&kp K_CUT` | - | Cut (Ctrl+X) |
| `&kp K_UNDO` | - | Undo (Ctrl+Z) |
| `&kp K_REDO` | - | Redo (Ctrl+Y) |
| `&kp PRINTSCREEN` | `&kp PSCRN` | Print Screen |
| `&kp SCROLLLOCK` | `&kp SLCK` | Scroll Lock |
| `&kp PAUSE_BREAK` | - | Pause/Break |

</details>

---

## 🔄 Layer Management

Layers let you access multiple key layouts on a single keyboard.

### Layer Behaviors

| Syntax | Name | Behavior | Example |
|--------|------|----------|---------|
| `&mo` | **Momentary** | Hold to activate layer | `&mo 1` |
| `&lt` | **Layer-Tap** | Tap for key, hold for layer | `&lt 2 TAB` |
| `&to` | **To Layer** | Switch permanently | `&to 0` |
| `&tog` | **Toggle** | Toggle layer on/off | `&tog 1` |
| `&sl` | **Sticky Layer** | Next key uses this layer | `&sl 2` |

### 💡 Usage Examples

```c
// Momentary layer (most common)
&mo 1              // Hold to activate layer 1, release to return

// Layer-tap (dual function)
&lt 2 TAB          // Tap: TAB, Hold: activate layer 2

// Permanent switch
&to 0              // Switch to base layer (layer 0) permanently

// Toggle layer
&tog 1             // Press once to enable layer 1, press again to disable

// Sticky layer (one-shot)
&sl 2              // Next single key press uses layer 2, then returns
```

### 🎯 When to Use Each

- **`&mo`**: Your daily driver - hold thumb key for symbols/numbers
- **`&lt`**: Dual-purpose keys - tab is tab, hold for layer
- **`&to`**: Gaming layers or mode switching
- **`&tog`**: Caps lock style layer enabling
- **`&sl`**: One-shot layers for quick symbol access

---

## 🎛️ Modifier Behaviors

Add modifiers to your keys without dedicated modifier keys.

### Modifier Behaviors

| Syntax | Name | Behavior | Example |
|--------|------|----------|---------|
| `&mt` | **Mod-Tap** | Tap for key, hold for modifier | `&mt LCTRL A` |
| `&sk` | **Sticky Key** | Modifier applies to next key only | `&sk LSHIFT` |

### 💡 Usage Examples

```c
// Mod-tap (dual function)
&mt LSHIFT SPACE   // Tap: space, Hold: shift
&mt LCTRL ESC      // Tap: escape, Hold: control
&mt LGUI TAB       // Tap: tab, Hold: GUI/Command

// Sticky key (one-shot modifier)
&sk LSHIFT         // Next key will be shifted, then auto-release
&sk LCTRL          // Next key will be Ctrl+[key], then auto-release
```

### 🎯 Common Patterns

```c
// Home row mods (advanced)
&mt LGUI A         // Tap A, hold for GUI (see custom behaviors section)
&mt LSHIFT S       // Tap S, hold for Shift

// Thumb modifiers
&mt LSHIFT SPACE   // Space/Shift on thumb
&mt LCTRL ESC      // Esc/Ctrl combo
```

---

## 📡 Bluetooth Controls

Manage Bluetooth connections to multiple devices.

### Bluetooth Behaviors

| Syntax | Description | Use Case |
|--------|-------------|----------|
| `&bt BT_SEL 0` | Connect to slot 0 | Switch to your laptop |
| `&bt BT_SEL 1` | Connect to slot 1 | Switch to your tablet |
| `&bt BT_SEL 2` | Connect to slot 2 | Switch to your phone |
| `&bt BT_SEL 3` | Connect to slot 3 | Fourth device |
| `&bt BT_SEL 4` | Connect to slot 4 | Fifth device |
| `&bt BT_CLR` | Clear current connection | Forget this device |
| `&bt BT_CLR_ALL` | Clear all connections | Reset all pairings |
| `&bt BT_NXT` | Next device | Cycle to next paired device |
| `&bt BT_PRV` | Previous device | Cycle to previous device |

### 💡 Usage Examples

```c
&bt BT_SEL 0       // Connect to first paired device (e.g., laptop)
&bt BT_SEL 1       // Connect to second paired device (e.g., tablet)
&bt BT_SEL 2       // Connect to third paired device (e.g., phone)

&bt BT_CLR         // Forget/unpair current device
&bt BT_CLR_ALL     // Clear all paired devices (useful for troubleshooting)

&bt BT_NXT         // Quick switch to next device
&bt BT_PRV         // Quick switch to previous device
```

### 🎯 Typical Setup

Most users dedicate a layer for Bluetooth controls:

```c
// On your SYSTEM/ADJUST layer
&bt BT_SEL 0  &bt BT_SEL 1  &bt BT_SEL 2  &bt BT_CLR  &bt BT_CLR_ALL
```

---

## 🛠️ Custom Behaviors

Advanced behaviors you can define in your keymap. These require configuration in the `behaviors` section.

### 1. 🏠 Homerow Mods (`&hm`)

**Tap for letter, hold for modifier** - the ultimate space-saver!

<details>
<summary><b>📖 Click to see configuration</b></summary>

```c
behaviors {
    hm: homerow_mods {
        compatible = "zmk,behavior-hold-tap";
        label = "HOMEROW_MODS";
        #binding-cells = <2>;
        tapping-term-ms = <200>;      // How long to hold for modifier
        quick-tap-ms = <180>;          // Prevent accidental holds when typing fast
        flavor = "tap-preferred";      // Prefer tap over hold
        bindings = <&kp>, <&kp>;       // First param is hold, second is tap
        global-quick-tap;              // Enable quick-tap across all keys
    };
};
```

</details>

**Usage:**
```c
&hm LGUI A         // Tap: A, Hold: Left GUI/Command
&hm LSHIFT S       // Tap: S, Hold: Left Shift
&hm LALT D         // Tap: D, Hold: Left Alt
&hm LCTRL F        // Tap: F, Hold: Left Control
```

**Why use it?** Access modifiers without leaving the home row!

---

### 2. 🎵 Tap Dance (`&para`)

**Multiple taps = different outputs**

<details>
<summary><b>📖 Click to see configuration</b></summary>

```c
behaviors {
    para: para {
        compatible = "zmk,behavior-tap-dance";
        label = "PARA";
        #binding-cells = <0>;
        bindings = <&kp LEFT_PARENTHESIS>, <&kp RIGHT_PARENTHESIS>;
    };
};
```

</details>

**Usage:**
```c
&para              // First tap: (, Second tap: )
```

**Example use cases:**
- Parentheses: `(` → `)`
- Brackets: `[` → `]`
- Quotes: `'` → `"`

---

### 3. 🔤 Caps Word (`&caps`)

**Auto-capitalize words, release on space**

<details>
<summary><b>📖 Click to see configuration</b></summary>

```c
behaviors {
    caps: caps {
        compatible = "zmk,behavior-caps-word";
        label = "CAPS";
        #binding-cells = <0>;
        continue-list = <MINUS BACKSPACE>;  // Don't cancel on these keys
    };
};
```

</details>

**Usage:**
```c
&caps              // Type LIKE_THIS until space/punctuation
```

**Perfect for:** `CONSTANT_NAMES`, `SCREAMING_SNAKE_CASE`, `FILE_NAMES`

---

### 4. 🔄 Mod-Morph (`&paraless`, `&paragreat`)

**Key changes based on active modifiers**

<details>
<summary><b>📖 Click to see configuration</b></summary>

```c
behaviors {
    paraless: paraless {
        compatible = "zmk,behavior-mod-morph";
        label = "PARALESS";
        bindings = <&kp LEFT_PARENTHESIS>, <&kp LESS_THAN>;
        #binding-cells = <0>;
        mods = <(MOD_LSFT)>;  // Morph when shift is held
    };
    
    paragreat: paragreat {
        compatible = "zmk,behavior-mod-morph";
        label = "PARAGREAT";
        bindings = <&kp RIGHT_PARENTHESIS>, <&kp GREATER_THAN>;
        #binding-cells = <0>;
        mods = <(MOD_LSFT)>;
    };
};
```

</details>

**Usage:**
```c
&paraless          // Normal: (, With Shift: <
&paragreat         // Normal: ), With Shift: >
```

**Why use it?** Get more symbols without extra layers!

---

## 🎬 Macros

Execute complex key sequences with a single keypress.

### Basic Macro Structure

```c
macros {
    macro_name: macro_name {
        compatible = "zmk,behavior-macro";
        label = "MACRO_NAME";
        #binding-cells = <0>;
        wait-ms = <10>;        // Delay between actions (milliseconds)
        tap-ms = <10>;         // How long to hold each key (milliseconds)
        bindings = <&kp H &kp E &kp L &kp L &kp O>;
    };
};
```

### Macro Actions

| Action | Description | Example |
|--------|-------------|---------|
| `&macro_tap` | Press and release | `&macro_tap &kp A` |
| `&macro_press` | Press and hold | `&macro_press &kp LSHIFT` |
| `&macro_release` | Release a key | `&macro_release &kp LSHIFT` |
| `&macro_pause_for_release` | Wait until macro key is released | Used with hold behaviors |
| `&macro_wait_time` | Wait N milliseconds | `&macro_wait_time 100` |

---

### 🔥 Hyper Key Macro (Most Useful!)

The **Hyper key** = `Ctrl + Shift + Alt + GUI` all at once.

**Why?** Creates unique key combinations that will NEVER conflict with existing shortcuts!

<details>
<summary><b>📖 Click to see Hyper key configuration</b></summary>

```c
macros {
    // Hold for Hyper modifier
    hyper: hyper {
        compatible = "zmk,behavior-macro";
        label = "HYPER";
        #binding-cells = <0>;
        bindings = <&macro_press &kp LCTRL &kp LSHIFT &kp LALT &kp LGUI>
                 , <&macro_pause_for_release>
                 , <&macro_release &kp LCTRL &kp LSHIFT &kp LALT &kp LGUI>;
    };
    
    // Hyper + F (for VSCode find)
    hyper_f: hyper_f {
        compatible = "zmk,behavior-macro";
        label = "HYPER_F";
        #binding-cells = <0>;
        bindings = <&macro_press &kp LCTRL &kp LSHIFT &kp LALT &kp LGUI>
                 , <&macro_tap &kp F>
                 , <&macro_release &kp LCTRL &kp LSHIFT &kp LALT &kp LGUI>;
    };
    
    // Hyper + R (for VSCode find/replace)
    hyper_r: hyper_r {
        compatible = "zmk,behavior-macro";
        label = "HYPER_R";
        #binding-cells = <0>;
        bindings = <&macro_press &kp LCTRL &kp LSHIFT &kp LALT &kp LGUI>
                 , <&macro_tap &kp R>
                 , <&macro_release &kp LCTRL &kp LSHIFT &kp LALT &kp LGUI>;
    };
    
    // Hyper + G (for VSCode global search)
    hyper_g: hyper_g {
        compatible = "zmk,behavior-macro";
        label = "HYPER_G";
        #binding-cells = <0>;
        bindings = <&macro_press &kp LCTRL &kp LSHIFT &kp LALT &kp LGUI>
                 , <&macro_tap &kp G>
                 , <&macro_release &kp LCTRL &kp LSHIFT &kp LALT &kp LGUI>;
    };
};
```

</details>

**Use in your keymap:**
```c
&hyper_f    // VSCode: Find
&hyper_r    // VSCode: Replace
&hyper_g    // VSCode: Global search
```

---

### 💡 Common Macro Patterns

<details>
<summary><b>Email/Username Macro</b></summary>

```c
email: email {
    compatible = "zmk,behavior-macro";
    label = "EMAIL";
    #binding-cells = <0>;
    bindings = <&kp M &kp Y &kp E &kp M &kp A &kp I &kp L 
                &kp AT 
                &kp E &kp X &kp A &kp M &kp P &kp L &kp E 
                &kp DOT 
                &kp C &kp O &kp M>;
};
```

</details>

<details>
<summary><b>Window Management Macro</b></summary>

```c
window_left: window_left {
    compatible = "zmk,behavior-macro";
    label = "WINDOW_LEFT";
    #binding-cells = <0>;
    bindings = <&macro_press &kp LGUI>
             , <&macro_tap &kp LEFT>
             , <&macro_release &kp LGUI>;
};
```

</details>

<details>
<summary><b>Screenshot Macro</b></summary>

```c
screenshot: screenshot {
    compatible = "zmk,behavior-macro";
    label = "SCREENSHOT";
    #binding-cells = <0>;
    bindings = <&macro_press &kp LGUI &kp LSHIFT>
             , <&macro_tap &kp N4>
             , <&macro_release &kp LGUI &kp LSHIFT>;
};
```

</details>

---

## 🔗 Combos

Press multiple keys together to trigger an action.

### Basic Combo Structure

```c
combos {
    compatible = "zmk,combos";
    
    combo_name {
        bindings = <&kp ESCAPE>;      // What happens
        key-positions = <13 29>;       // Which keys (by position)
        timeout-ms = <50>;             // Optional: timing window
        layers = <0 1>;                // Optional: active only on these layers
    };
};
```

---

### 🗺️ Key Position Reference (Corne)

```
Left Hand:                    Right Hand:
 0   1   2   3   4   5        6   7   8   9  10  11
12  13  14  15  16  17       18  19  20  21  22  23
24  25  26  27  28  29       30  31  32  33  34  35
            36  37  38       39  40  41
```

---

### 💡 Your Current Combos Explained

<details>
<summary><b>📖 Click to see all your current combos</b></summary>

```c
// ESC: Middle fingers home row
escape {
    bindings = <&kp ESCAPE>;
    key-positions = <13 29>;        // D + K positions
}

// DELETE: Index fingers upper row
delete {
    bindings = <&kp DELETE>;
    key-positions = <15 21>;        // F + L positions
}

// COPY: Ring + middle finger on lower right
copy {
    bindings = <&kp K_COPY>;        // Ctrl+C
    key-positions = <28 27>;
}

// PASTE: Pinky + ring finger on lower right
paste {
    bindings = <&kp K_PASTE>;       // Ctrl+V
    key-positions = <26 27>;
}

// Symbols via combos
percent {
    bindings = <&kp PERCENT>;       // %
    key-positions = <5 17>;
}

equal {
    bindings = <&kp EQUAL>;         // =
    key-positions = <28 16>;
}

// ... and more symbol combos
```

</details>

---

### 🎯 Common Combo Patterns

<details>
<summary><b>Home Row Combos</b></summary>

```c
// Press J+K together for ESC
jk_esc {
    bindings = <&kp ESC>;
    key-positions = <19 20>;
}

// Press D+F together for TAB
df_tab {
    bindings = <&kp TAB>;
    key-positions = <14 15>;
}
```

</details>

<details>
<summary><b>Vertical Combos</b></summary>

```c
// Press Q+A together for SHIFT
qa_shift {
    bindings = <&sk LSHIFT>;
    key-positions = <0 12>;
}
```

</details>

<details>
<summary><b>Adjacent Key Combos</b></summary>

```c
// Press U+I together for BACKSPACE
ui_bspc {
    bindings = <&kp BSPC>;
    key-positions = <7 8>;
}
```

</details>

---

### ⚙️ Combo Settings

- **`timeout-ms`**: How long to wait for simultaneous press (default: 50ms)
  - Lower (20-30ms): More intentional, less accidental
  - Higher (50-80ms): More forgiving, easier to trigger
- **`layers`**: Restrict combo to specific layers
  - Omit for "works on all layers"
  - `layers = <0>;` for "base layer only"

---

## 🔀 Conditional Layers

Auto-activate a layer when multiple other layers are active.

### Structure

```c
conditional_layers {
    compatible = "zmk,conditional-layers";
    
    layer_name {
        if-layers = <1 2>;     // When layers 1 AND 2 are active
        then-layer = <3>;      // Automatically activate layer 3
    };
};
```

### 💡 Your Current Setup

```c
conditional_layers {
    compatible = "zmk,conditional-layers";
    
    l3 {
        if-layers = <1 2>;     // NAV + SYM layers
        then-layer = <3>;      // Activates ADJUST layer
    };
};
```

**What this means:**
- Hold NAV layer key (layer 1)
- Hold SYM layer key (layer 2)
- **Result:** ADJUST layer (layer 3) automatically activates!

### 🎯 Why Use Conditional Layers?

- Access system functions without dedicating a key
- Natural progression: symbols → numbers → system
- No "dead" thumb key combinations

---

## 📝 Your Current Setup Reference

Quick overview of your existing Corne configuration.

### Layer Structure

| Layer | Name | Purpose | Access |
|-------|------|---------|--------|
| **0** | DEF (Default) | Base typing layer | Always active |
| **1** | NAV (Navigation) | Numbers & navigation | `&mo 1` (thumb) |
| **2** | SYM (Symbols) | Symbols & punctuation | `&lt 2 TAB` (thumb) |
| **3** | ADJ (Adjust) | F-keys, BT, system | NAV + SYM together |
| **4** | FUNC (Function) | Empty (ready for Hyper keys!) | Not currently accessible |

---

### 🏠 Homerow Mods (Layer 0)

Your home row has dual functionality:

**Left Hand:**
```
A - Tap: A, Hold: GUI
S - Tap: S, Hold: SHIFT
D - Tap: D, Hold: ALT
F - Tap: F, Hold: CTRL
```

**Right Hand:**
```
J - Tap: J, Hold: CTRL
K - Tap: K, Hold: ALT
L - Tap: L, Hold: SHIFT
; - Tap: ;, Hold: GUI
```

---

### 🎯 Access Patterns

```c
// Layer 1 (NAV)
Hold left thumb → &mo 1

// Layer 2 (SYM)
Tap right thumb = TAB
Hold right thumb → &lt 2 TAB

// Layer 3 (ADJ)
Hold BOTH layer keys together (automatic via conditional layers)

// Layer 4 (FUNC) - Currently not accessible!
// Add &mo 4 or &tog 4 somewhere to use it
```

---

### ⚡ Quick Reference Visual

```
┌─── Layer 0 (DEF) ───┐
│  Base typing layout  │
│  Homerow mods active │
└──────────────────────┘
         ↓ Hold thumb
┌─── Layer 1 (NAV) ────┐
│  Numbers 1-0         │
│  Arrow keys          │
│  Page Up/Down        │
└──────────────────────┘
         +
┌─── Layer 2 (SYM) ────┐
│  Symbols ! @ # $ %   │
│  Brackets [ ] { }    │
│  Operators + - * /   │
└──────────────────────┘
         ↓ Both held
┌─── Layer 3 (ADJ) ────┐
│  F1-F12 keys         │
│  Bluetooth controls  │
│  Bootloader          │
└──────────────────────┘
```

---

## 💡 Common Patterns

Real-world examples and best practices.

### 🎮 VSCode with Hyper Key

After adding Hyper macros to your keyboard:

**In your keymap:**
```c
&hyper_f  // Find in file
&hyper_r  // Find and replace
&hyper_g  // Global search
&hyper_d  // Multi-cursor next match
```

**In VSCode `keybindings.json`:**
```json
[
  {
    "key": "ctrl+shift+alt+cmd+f",
    "command": "actions.find",
    "when": "editorFocus"
  },
  {
    "key": "ctrl+shift+alt+cmd+r",
    "command": "editor.action.startFindReplaceAction"
  },
  {
    "key": "ctrl+shift+alt+cmd+g",
    "command": "workbench.action.findInFiles"
  }
]
```

**Why it works:** Vim can't intercept `Ctrl+Shift+Alt+Cmd+F` because nothing uses that combo!

---

### 🎯 Gaming Layer

Disable homerow mods for gaming:

```c
GAME {
    bindings = <
        &kp TAB   &kp Q  &kp W  &kp E  &kp R  &kp T    ...
        &kp LSHFT &kp A  &kp S  &kp D  &kp F  &kp G    ...
        &kp LCTRL &kp Z  &kp X  &kp C  &kp V  &kp B    ...
                        &kp LGUI &kp SPACE &mo 1
    >;
}
```

Access with: `&to 4` (permanent switch), return with `&to 0`

---

### ✍️ Vim-Style Navigation

Add to your NAV layer:

```c
&kp H  &kp J  &kp K  &kp L    // Move like Vim hjkl
```

Or use combos for arrow keys anywhere:

```c
jk_up {
    bindings = <&kp UP>;
    key-positions = <19 20>;  // J+K = Up
}
```

---

### 🔢 Number Row Alternatives

**Option 1: Dedicated Number Layer**
```c
&kp N1 &kp N2 &kp N3 &kp N4 &kp N5    // Top row of NAV layer
```

**Option 2: Numpad Style**
```c
&kp N7 &kp N8 &kp N9
&kp N4 &kp N5 &kp N6
&kp N1 &kp N2 &kp N3
       &kp N0
```

**Option 3: Home Row Numbers** (very advanced!)
```c
&hm N1 A  &hm N2 S  &hm N3 D  &hm N4 F  &hm N5 G
```

---

### 🖱️ Mouse Keys (Future Feature)

ZMK doesn't support mouse keys yet, but you can use:
- **AutoHotkey** (Windows)
- **Karabiner-Elements** (macOS)
- **xdotool** (Linux)

To translate Hyper+keys into mouse movements!

---

## ✨ Tips & Best Practices

Level up your ZMK game with these pro tips!

### 🎓 For Beginners

<details>
<summary><b>1. Start Simple</b></summary>

Don't add everything at once! Start with:
1. Basic key presses (`&kp`)
2. One layer for numbers/symbols (`&mo`)
3. Gradually add homerow mods
4. Then experiment with combos

**Rule of thumb:** If you can't remember what a key does, it's too complex!

</details>

<details>
<summary><b>2. Test Before Flashing</b></summary>

- Use the [ZMK Keymap Editor](https://nickcoutsos.github.io/keymap-editor/) for visual editing
- Build your `.keymap` locally and check for errors
- Keep a working backup before making major changes

</details>

<details>
<summary><b>3. Use Meaningful Layer Names</b></summary>

```c
#define BASE 0    // ❌ Generic
#define DEF 0     // ✅ Clear

#define L1 1      // ❌ Meaningless
#define NAV 1     // ✅ Descriptive
```

</details>

---

### ⚡ For Intermediate Users

<details>
<summary><b>1. Optimize Homerow Mod Timing</b></summary>

Adjust `tapping-term-ms` to match your typing speed:
- **Fast typers**: 150-175ms
- **Average typers**: 175-200ms  
- **Slow/deliberate typers**: 200-250ms

Too low → accidental mods  
Too high → slow to activate

</details>

<details>
<summary><b>2. Layer Through to Reduce Definitions</b></summary>

Use `&trans` liberally! Don't redefine every key on every layer.

```c
// ❌ Bad: Redefining everything
SYM {
    bindings = <
        &kp EXCL &kp AT &kp HASH ... &kp Q &kp W &kp E &kp R ...
    >;
}

// ✅ Good: Only define what changes
SYM {
    bindings = <
        &kp EXCL &kp AT &kp HASH ... &trans &trans &trans &trans ...
    >;
}
```

</details>

<details>
<summary><b>3. Combo Timeout Sweet Spot</b></summary>

- **20-30ms**: Intentional, minimal false triggers
- **40-50ms**: Balanced (recommended)
- **60-80ms**: Forgiving, more false triggers

Start at 50ms, adjust based on feel.

</details>

---

### 🚀 For Advanced Users

<details>
<summary><b>1. Layer Organization Patterns</b></summary>

**The "Tri-Layer" Pattern:**
```c
Layer 0: Letters (BASE)
Layer 1: Numbers/Nav (Hold left thumb)
Layer 2: Symbols (Hold right thumb)
Layer 3: Function/System (Both thumbs via conditional)
```

**The "Callum" Pattern:**
```c
Layer 0: Letters with homerow mods
Layer 1: Numbers on left, nav on right
Layer 2: Symbols mirroring number layer
Layer 3: Function keys
```

</details>

<details>
<summary><b>2. Macro Optimization</b></summary>

```c
// ❌ Inefficient
&macro_tap &kp L &kp O &kp N &kp G
&macro_wait_time 100  
&macro_tap &kp S &kp T &kp R &kp I &kp N &kp G

// ✅ Better
wait-ms = <5>;   // Set globally
tap-ms = <5>;
bindings = <&kp L &kp O &kp N &kp G 
            &macro_wait_time 100
            &kp S &kp T &kp R &kp I &kp N &kp G>;
```

</details>

<details>
<summary><b>3. Debugging Tips</b></summary>

**Check your build logs:**
```bash
# In your ZMK config repo
git push  # Triggers GitHub Action
# Check Actions tab for build errors
```

**Common errors:**
- Missing comma in bindings
- Wrong number of keys in layer
- Undefined behavior references
- Duplicate combo key-positions

</details>

---

### 💎 Pro Tips

| Tip | Why |
|-----|-----|
| **Keep `&to 0` accessible** | Always have a way back to base layer! |
| **Test macros offline first** | Use keyboard tester websites |
| **Document your layout** | Future you will thank present you |
| **Version control your `.keymap`** | Git is your friend! |
| **One change at a time** | Easier to debug what broke |
| **Physical layout != Logical layout** | Your brain adapts to muscle memory |

---

## 🔗 Resources

### Official Documentation
- [**ZMK Documentation**](https://zmk.dev/docs) - Official docs (start here!)
- [**Behavior Reference**](https://zmk.dev/docs/behaviors/hold-tap) - Deep dive into behaviors
- [**Key Codes**](https://zmk.dev/docs/codes) - Complete key code list
- [**GitHub Repo**](https://github.com/zmkfirmware/zmk) - Source code & issues

### Tools & Editors
- [**Keymap Editor**](https://nickcoutsos.github.io/keymap-editor/) - Visual keymap builder (best for beginners!)
- [**Keyboard Layout Comparison**](https://jhelvy.shinyapps.io/splitkbcompare/) - Compare keyboard layouts
- [**Keyboard Tester**](https://www.keyboardtester.com/) - Test your keyboard output

### Community
- [**ZMK Discord**](https://zmk.dev/community/discord/discord-invite) - Active community, get help!
- [**r/ErgoMechKeyboards**](https://reddit.com/r/ErgoMechKeyboards) - Reddit community
- [**Awesome ZMK**](https://github.com/urob/awesome-zmk) - Curated list of configs & resources

### Example Configs
- [**urob's config**](https://github.com/urob/zmk-config) - Advanced homerow mods
- [**caksoylar's config**](https://github.com/caksoylar/zmk-config) - Great combos & layers
- [**Your config**](.) - You're building this! 🎉

### Hardware
- [**Corne (CRKBD)**](https://github.com/foostan/crkbd) - Your keyboard!
- [**nice!nano**](https://nicekeyboards.com/nice-nano/) - Popular ZMK controller
- [**ZMK Supported Hardware**](https://zmk.dev/docs/hardware) - Full list

---

### 📚 Further Learning

**Want to go deeper?**
1. Read the [ZMK Behaviors](https://zmk.dev/docs/behaviors) docs thoroughly
2. Study other people's keymaps on GitHub
3. Join the Discord and ask questions
4. Experiment! The best way to learn is by doing

**Advanced Topics to Explore:**
- RGB Underglow configuration
- Display customization (if your board has one)
- Battery optimization
- Custom shields for new keyboards
- Contributing to ZMK development

---

## 🎉 You're Ready!

You now have a complete reference for ZMK firmware. Remember:

1. **Start simple** - Don't overcomplicate
2. **Iterate** - Small changes, test often  
3. **Document** - Future you will appreciate it
4. **Share** - Help others learn from your config!

**Happy typing! 🎹**

---

**Document Version:** 1.0  
**Last Updated:** February 14, 2026  
**Keyboard:** Corne (CRKBD)  
**Firmware:** ZMK

---

*Made with ❤️ for the mechanical keyboard community*
