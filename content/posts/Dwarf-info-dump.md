---
title: "Dwarf Info Dump"
date: 2023-04-19T16:18:36+08:00
draft: true
---
### Dwarf and Libdwarf

DWARF is a widely used, standardized debugging data format. Libdwarf is a C library intended to simplify reading (and writing) applications using DWARF2, DWARF3, DWARF4 and DWARF5. We can use [Libdwarf API](https://www.prevanders.net/libdwarfdoc/index.html) to extract programs' debugging information.

### addr2line

**addr2line** is a Linux command which translates addresses into file names and line numbers. Given an address in an executable or an offset in a section of a relocatable object, it uses the debugging information to figure out which file name and line number are associated with it. We can use Libdwarf and the implementation of addr2line to create an offline backtrace database for given objfiles.

### dwarf\_line\_info\_dump

`dwarf_line_info_dump` is a tool to dump the line information belongs to every address in all cu\_dies contains in Dwarf. The key is to map the given objfile name and offset to its line info back to source code. The file dumpped by `dwarf_line_info_dump` started with the target objfile name following by the line number, high\_addr and low\_addr which match with the line number, as well as offsets which point to the filename and symbol name in the bottom of the file.
