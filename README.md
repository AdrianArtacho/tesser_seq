# Tesser_seq

The goal of this device is to allow the performer to recall notes stores in midi files in different ways.

---

![img/gui.png](img/gui.png)

---

## Setup


---

## MODES

### Simple mode: note by note

When the performer hits a note (notes off messages are filtered), two things happen in rapid succession:

* A trigger note is send via OSC to a `tesser_pipe` device, which feeds it to an instance of **Synced pitch trigger V1**.

* Inmediately after, ticks are send to the [seq] object until a new, non note-off message is found. That will be sent by the device as midiout. This should be piped to the **Synced pitch trigger V1** device using a **Send MIDI notes via pipe** device.

This way, **Synced pitch trigger V1** receives two streams: one triggers last fed note, and the other feeds the next note to be triggered.

---