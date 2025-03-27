project('acorn', 'c')

qjsc_exe = find_program('qjsc')
qjs_dep = dependency('quickjs-ng')

acorn_c_headers = include_directories('include')

acorn_bytecode = custom_target(
    'acorn_bytecode',
    input: 'acorn/src/index.js',
    output: 'acorn-bytecode.c',
    command: [
        qjsc_exe,
        '-s',
        '-m',
        '-o', '@OUTPUT@',
        '-N', 'js_acorn_bytecode',
        '@INPUT@',
    ],
)

acorn_lib = library(
    'acorn',
    [acorn_bytecode],
    include_directories: acorn_c_headers,
    dependencies: qjs_dep,
)

acorn_dep = declare_dependency(
    link_with: acorn_lib,
    include_directories: acorn_c_headers,
    dependencies: qjs_dep,
)
