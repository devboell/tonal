<a name="module_note"></a>

# note
[![npm version](https://img.shields.io/npm/v/tonal-note.svg)](https://www.npmjs.com/package/tonal-note)
[![tonal](https://img.shields.io/badge/tonal-note-yellow.svg)](https://www.npmjs.com/browse/keyword/tonal)

`tonal-note` is a collection of functions to manipulate musical notes in scientific notation

This is part of [tonal](https://www.npmjs.com/package/tonal) music theory library.

## Usage

```js
import * as note from 'tonal-note'
// or const note = require('tonal-note')
note.name('bb2') // => 'Bb2'
note.chroma('bb2') // => 10
note.midi('a4') // => 69
note.freq('a4') // => 440
note.oct('G3') // => 3

// part of tonal
const tonal = require('tonal')
tonal.note.midi('d4') // => 62
```

## Install

[![npm install tonal-note](https://nodei.co/npm/tonal-note.png?mini=true)](https://npmjs.org/package/tonal-note/)

## API Documentation


* [note](#module_note)
    * [`.isNote`](#module_note.isNote) ⇒ <code>boolean</code>
    * [`.midiToFreq`](#module_note.midiToFreq) ⇒ <code>Number</code>
    * [`.freqToMidi`](#module_note.freqToMidi) ⇒ <code>Number</code>
    * [`.chroma`](#module_note.chroma) ⇒ <code>Integer</code>
    * [`.stepToLetter`](#module_note.stepToLetter) ⇒ <code>string</code>
    * [`.altToAcc`](#module_note.altToAcc) ⇒ <code>String</code>
    * [`.name()`](#module_note.name) ⇒ <code>string</code>
    * [`.pc()`](#module_note.pc) ⇒ <code>string</code>
    * [`.midi(note)`](#module_note.midi) ⇒ <code>Integer</code>
    * [`.freq(note)`](#module_note.freq) ⇒ <code>Number</code>
    * [`.oct(note)`](#module_note.oct) ⇒ <code>Integer</code>
    * [`.step(note)`](#module_note.step) ⇒ <code>Integer</code>
    * [`.alt(note)`](#module_note.alt) ⇒ <code>Integer</code>
    * [`.fromMidi(midi, [boolean])`](#module_note.fromMidi) ⇒ <code>string</code>

<a name="module_note.isNote"></a>

## `note.isNote` ⇒ <code>boolean</code>
Test if the given string is a note

**Kind**: static constant of [<code>note</code>](#module_note)  

| Param | Type |
| --- | --- |
| name | <code>String</code> | 

<a name="module_note.midiToFreq"></a>

## `note.midiToFreq` ⇒ <code>Number</code>
Get the frequency from midi number

**Kind**: static constant of [<code>note</code>](#module_note)  
**Returns**: <code>Number</code> - the frequency or null if not valid note midi  

| Param | Type | Description |
| --- | --- | --- |
| midi | <code>Number</code> | the note midi number |
| tuning | <code>Number</code> | (Optional) 440 by default |

<a name="module_note.freqToMidi"></a>

## `note.freqToMidi` ⇒ <code>Number</code>
Get the midi number from a frequency in hertz. The midi number can
contain decimals (with two digits precission)

**Kind**: static constant of [<code>note</code>](#module_note)  

| Param | Type |
| --- | --- |
| frequency | <code>Number</code> | 

**Example**  
```js
note.freqToMidi(220)); //=> 57;
note.freqToMidi(261.62)); //=> 60;
note.freqToMidi(261)); //=> 59.96;
```
<a name="module_note.chroma"></a>

## `note.chroma` ⇒ <code>Integer</code>
Return the chroma of a note. The chroma is the numeric equivalent to the
pitch class, where 0 is C, 1 is C# or Db, 2 is D... 11 is B

**Kind**: static constant of [<code>note</code>](#module_note)  
**Returns**: <code>Integer</code> - the chroma number  

| Param | Type | Description |
| --- | --- | --- |
| note | <code>string</code> | the note name |

**Example**  
```js
const note = require('tonal-note')
note.chroma('Cb') // => 11
['C', 'D', 'E', 'F'].map(note.chroma) // => [0, 2, 4, 5]
```
<a name="module_note.stepToLetter"></a>

## `note.stepToLetter` ⇒ <code>string</code>
Given a step number return it's letter (0 = C, 1 = D, 2 = E)

**Kind**: static constant of [<code>note</code>](#module_note)  
**Returns**: <code>string</code> - the letter  

| Param | Type |
| --- | --- |
| step | <code>number</code> | 

**Example**  
```js
note.stepToLetter(3) // => "F"
```
<a name="module_note.altToAcc"></a>

## `note.altToAcc` ⇒ <code>String</code>
Given an alteration number, return the accidentals

**Kind**: static constant of [<code>note</code>](#module_note)  

| Param | Type |
| --- | --- |
| alt | <code>Number</code> | 

**Example**  
```js
note.altToAcc(-3) // => 'bbb'
```
<a name="module_note.name"></a>

## `note.name()` ⇒ <code>string</code>
Given a note name, return the note name or null if not valid note.
The note name will ALWAYS have the letter in upercase and accidentals
using # or b

Can be used to test if a string is a valid note name.

**Kind**: static method of [<code>note</code>](#module_note)  

| Type |
| --- |
| <code>Pitch</code> \| <code>string</code> | 

**Example**  
```js
const note = require('tonal-note')
note.name('cb2') // => 'Cb2'
['c', 'db3', '2', 'g+', 'gx4'].map(note.name) // => ['C', 'Db3', null, null, 'G##4']
```
<a name="module_note.pc"></a>

## `note.pc()` ⇒ <code>string</code>
Get pitch class of a note. The note can be a string or a pitch array.

**Kind**: static method of [<code>note</code>](#module_note)  
**Returns**: <code>string</code> - the pitch class  

| Type |
| --- |
| <code>string</code> \| <code>Pitch</code> | 

**Example**  
```js
tonal.pc('Db3') // => 'Db'
tonal.map(tonal.pc, 'db3 bb6 fx2') // => [ 'Db', 'Bb', 'F##']
```
<a name="module_note.midi"></a>

## `note.midi(note)` ⇒ <code>Integer</code>
Get the note midi number
(an alias of tonal-midi `toMidi` function)

**Kind**: static method of [<code>note</code>](#module_note)  
**Returns**: <code>Integer</code> - the midi number or null if not valid pitch  
**See**: midi.toMidi  

| Param | Type | Description |
| --- | --- | --- |
| note | <code>string</code> \| <code>Number</code> | the note to get the midi number from |

**Example**  
```js
note.midi('C4') // => 60
note.midi(60) // => 60
```
<a name="module_note.freq"></a>

## `note.freq(note)` ⇒ <code>Number</code>
Get the frequency of a note

**Kind**: static method of [<code>note</code>](#module_note)  
**Returns**: <code>Number</code> - the frequency  

| Param | Type | Description |
| --- | --- | --- |
| note | <code>string</code> \| <code>Number</code> | the note name or midi note number |

**Example**  
```js
note.freq('A4') // => 440
note.freq(69) // => 440
```
<a name="module_note.oct"></a>

## `note.oct(note)` ⇒ <code>Integer</code>
Get the octave of the given pitch

**Kind**: static method of [<code>note</code>](#module_note)  
**Returns**: <code>Integer</code> - the octave or null if doesn't have an octave or not a valid note  

| Param | Type | Description |
| --- | --- | --- |
| note | <code>string</code> | the note |

**Example**  
```js
note.oct('C#4') // => 4
note.oct('C') // => null
note.oct('blah') // => undefined
```
<a name="module_note.step"></a>

## `note.step(note)` ⇒ <code>Integer</code>
Get the note step: a number equivalent of the note letter. 0 means C and
6 means B. This is different from `chroma` (see example)

**Kind**: static method of [<code>note</code>](#module_note)  
**Returns**: <code>Integer</code> - a number between 0 and 6 or null if not a note  

| Param | Type | Description |
| --- | --- | --- |
| note | <code>string</code> | the note |

**Example**  
```js
note.step('C') // => 0
note.step('Cb') // => 0
// usually what you need is chroma
note.chroma('Cb') // => 6
```
<a name="module_note.alt"></a>

## `note.alt(note)` ⇒ <code>Integer</code>
Get the note alteration: a number equivalent to the accidentals. 0 means
no accidentals, negative numbers are for flats, positive for sharps

**Kind**: static method of [<code>note</code>](#module_note)  
**Returns**: <code>Integer</code> - the alteration  

| Param | Type | Description |
| --- | --- | --- |
| note | <code>string</code> \| <code>Pitch</code> | the note |

**Example**  
```js
note.alt('C') // => 0
note.alt('C#') // => 1
note.alt('Cb') // => -1
```
<a name="module_note.fromMidi"></a>

## `note.fromMidi(midi, [boolean])` ⇒ <code>string</code>
Given a midi number, returns a note name. The altered notes will have
flats unless explicitly set with the optional `useSharps` parameter.

**Kind**: static method of [<code>note</code>](#module_note)  
**Returns**: <code>string</code> - the note name  

| Param | Type | Description |
| --- | --- | --- |
| midi | <code>number</code> | the midi note number |
| [boolean] |  | useSharps - (Optional) set to true to use sharps instead of flats |

**Example**  
```js
const note = require('tonal-note')
note.fromMidi(61) // => 'Db4'
note.fromMidi(61, true) // => 'C#4'
// it rounds to nearest note
note.fromMidi(61.7) // => 'D4'
```
