---
title: The difference between CommonJS modularisation and ES6 modularisation
date: 2021-01-02 22:52:24
tags:
  - front-end brief
---

### **Module loading**

- `CommonJS` mainly relies on environment variables like `module`, `exports`, `requrire` and `global`. It loads modules synchronously.
- `ES6` modules are not objects. The `import` clause will be dynamically parsed by JavaScript engine when compiling. And code in each module will be introduced during compiling rather than in the runtime. Therefore, it cannot be used in conditional loading scenario. On the other hand, due to the limitation, it makes static analyse possible.

### **Value VS Reference**

- A `CommonJS` module outputs a copy of a module. That is, once a value is output, changes within the output module will not affect the original module.
- An `ES6` module outputs a reference of a value. That is, when JavaScript engine statically analyses scripts, it will produce a read-only reference when it encounters the module loading command `import`. When the script is actually executed, values will be taken from the loaded modules according to the read-only references. If the original value changes, the value `import`ed will also be changed. Therefore, the `ES6` module is a dynamic reference and does not cache values. Variables in the module are bound to the original module in which they are located.

### **When the module is loading**

- Runtime loading: each `CommonJS` module is an object. That is, when `require` the module, whole module is loaded at first and produced as an object, and then methods are read from the object. `CommonJS` loads an object (i.e `module.exports` command). The object is generated only after the script has been run.
- Compile-time loading: `ES6` module is not an object, but it uses `export` command to specify code that need to be exported. The static command `export` is used when `import`ing specific code. That is, when `import`ing, you can specify an output value to load instead of loading the whole module. `ES6` module is not an object, its an external interface, which is just a static definition, which will be generated in the phase of static parsing during code compilation.
