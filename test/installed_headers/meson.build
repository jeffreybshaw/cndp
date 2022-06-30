# SPDX-License-Identifier: BSD-3-Clause
# Copyright (c) 2022 Intel Corporation

# This project is used to verify whether the headers installed by the
# 'make install' command can be compiled for C and C++ applications.

project('test_installed_headers', 'c', 'cpp')

dep = dependency('libcndp')

c = meson.get_compiler('c')
cpp = meson.get_compiler('cpp')

project_arguments = [
    '-fpermissive',
    '-D_GNU_SOURCE',
    '-Wno-address-of-packed-member',
    '-Wno-packed-not-aligned',
]

foreach arg: project_arguments
    if c.has_argument(arg)
        add_project_arguments(arg, language: 'c')
    endif
    if cpp.has_argument(arg)
        add_project_arguments(arg, language: 'cpp')
    endif
endforeach

testc = executable('testc', 'main.c', dependencies: dep)
testcpp = executable('testcpp', 'main.c', dependencies: dep)

test('testc', testc)
test('testcpp', testcpp)
