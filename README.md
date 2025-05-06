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

    -   `specialized_from<Type, Template>` -> concept

    -   `instantiable_with<Template, Args...>` -> concept

-   nya/join:

    -   `is_char<Type>` -> type trait
    
    -   `is_string<Type>` -> type trait

    -   `join_with<RangeType, StringType>(RangeType &&, StringType &&)` -> function template