

---

### Multiprogramming vs Multitasking

| Aspect               | **Multiprogramming**                                                                             | **Multitasking**                                                                                  |
| -------------------- | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------- |
| **Definition**       | Running **multiple programs** on a CPU, one at a time, with CPU switching when one waits for I/O | Running **multiple tasks/processes** seemingly at the same time by rapidly switching between them |
| **Purpose**          | Maximize CPU **utilization**                                                                     | Maximize **user responsiveness** and CPU usage                                                    |
| **Focus**            | **Efficient CPU use** while one job waits for I/O                                                | **Interactive user experience** with multiple programs                                            |
| **System Type**      | Used in **batch systems**                                                                        | Common in **time-sharing** or **interactive systems**                                             |
| **Concurrency**      | Not truly concurrent — only one program is active at a time                                      | Appears concurrent — fast context switching makes it feel simultaneous                            |
| **User Involvement** | Usually **non-interactive**, no direct user input                                                | Designed for **interactive use**, with user input/output                                          |
| **Example**          | Running compiler while printer is printing another job                                           | Browsing the web, playing music, and editing a document simultaneously                            |

---

###  **Simplified Analogy**:

* **Multiprogramming** = Like a chef cooking multiple meals — switches from one pot to another while waiting for one to boil.
* **Multitasking** = Like a user on a computer checking email, listening to music, and downloading a file — all happening "at once" from the user’s perspective.

