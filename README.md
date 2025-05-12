# Library NYA!

Useful tools by \_\_NYA\_\_.

## Install

Run command below in project root directory:

```
cmake -DCMAKE_INSTALL_PREFIX=/usr/local -B build && sudo cmake --install build
```

## Usage

Add these lines into your CMakeLists.txt file:

```
find_package(libnya REQUIRED)
target_link_libraries(<target-name> PRIVATE libnya::libnya)
```

You need to replace `<target-name>` with your target name.

## Contents

-   nya/type_traits:

    -   `is_specialization_of<Type, Template>` -> type trait

    -   `is_instantiable_with<Template, Args...>` -> type trait

    -   `is_template_prefix_equivalent<Template, N, Args...>` -> type trait

    -   `required_template_args<Template, Args...>` -> type trait

-   nya/concepts:

    -   `same_after_decay<Type1, Type2>` -> concept

    -   `specialized_from<Type, Template>` -> concept

    -   `instantiable_with<Template, Args...>` -> concept

-   nya/join:

    -   `is_char<Type>` -> type trait
    
    -   `is_string<Type>` -> type trait

    -   `join_with<RangeType, StringType>(RangeType &&, StringType &&)` -> function template

-   nya/cpp_codegen:

    -   `expression` -> class for representing and constructing C++ expressions

    -   `type` -> class for representing and constructing C++ types

    -   `cofstream` -> class for writing C++ file

    -   `expression operator""_expr(const char * str, size_t)` -> suffix for easily creating expression (with precedence `LOWEST`)

    -   `expression operator""_term(const char * str, size_t)` -> suffix for easily creating expression (with precedence `HIGHEST`)

    -   `expression operator""_lit(const char * str, size_t)` -> suffix for easily creating string literal (with precedence `HIGHEST`), ignorable

    -   `type operator""_type(const char * str, size_t)` suffix for easily creating type

    -   `create_cpp_*(...)` -> macros for creating blocks, based on RAII of `cofstream::scope_guard`

-   nya/factory:

    -   `factory<Type>` -> factory class of `Type`

    -   `REGISTER_CLASS(DerivedType, BaseType)` -> macro for registering class `DerivedType` to `factory<BaseType>`

-   nya/memory:

    -   `size_t align(size_t size, size_t alignment)` -> function for aligning size up to alignment

    -   `observer_ptr<Type>` -> class standing for a pointer that doesn't hold the resource