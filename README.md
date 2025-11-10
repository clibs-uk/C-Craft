# C-Craft

[![Version](https://img.shields.io/badge/version-1.0.1-blue)](https://www.clibs.co.uk/c-craft.html)

**C-Craft** is a feature-rich extension of the standard C library, providing robust memory management, generic data structures, and application utilities for production-ready C development.  
Developed by **C Libs**, it’s designed for developers who want modern functionality in plain C without external dependencies.

## Overview

C-Craft simplifies building C applications by providing a solid foundation of reusable components. It handles the repetitive infrastructure, collections, strings, memory scopes, and application utilities so you can focus on your core logic.

- **Product Page:** [https://www.clibs.co.uk/c-craft.html](https://www.clibs.co.uk/c-craft.html)  
- **Full Documentation:** [https://www.clibs.co.uk/doc/c-craft/index.html](https://www.clibs.co.uk/doc/c-craft/index.html)

## Features

- Scoped memory management: allocate freely and release entire scopes with a single call  
- Generic collections: lists, vectors, dictionaries, stacks, and queues, supporting both primitive and user-defined types  
- Enhanced string handling: join, split, search/replace, and regex-based operations  
- Application utilities: command-line parsing, configuration files, variable substitution, and logging  
- File and system tools: I/O helpers, date/time functions, random numbers, and hashing  
- No external dependencies: uses only standard C and Unix system calls

## Installation

1. Download the latest release from the [C-Craft product page](https://www.clibs.co.uk/c-craft.html).  
2. Extract the archive and build according to the documentation instructions.  
3. Include the required headers in your project, for example:

   ```c
   #include <c-craft/mem.h>
   #include <c-craft/list-double.h>
   ```
4. Link against the compiled library or include the relevant source files in your build.  

Full setup details are provided in the [documentation](https://www.clibs.co.uk/doc/c-craft/index.html).

## Example

Using scoped memory and a user defined struct:

```c
	#include <c-craft/mem.h>
	#include "stack-person.h"

	typedef struct person
	{
		char *name;
		char *address;
	}
	PERSON;

	MEM_SCOPE mem = sm_create(0);

	/* A stack with 10 initial slots. Slots expand on demand. */
	STACK_PERSON stk = stack_person_create(mem, 10);

	PERSON *person = sm_alloc(mem, sizeof(person));
	person->name = sm_strdup(mem, "Jim Smith");
	person->address = sm_strdup(mem, "10 Acacia Avenue");

	stack_person_push(stk, person);

	person = sm_alloc(mem, sizeof(person));
	person->name = "Rose Jones";
	person->address = "5 High Street"

	stack_person_push(stk, person);

	/* ...  do some work etc... */

	sm_free(mem); /* Frees persons, names and addresses also */
```

Creating a container for a custom type:

```c
#define TYPE struct person *
#define NAME person
#define UNAME PERSON
#include <c-craft/stack-decl.h>
#undef TYPE
#undef NAME
#undef UNAME
```

More examples and API details are available in the [Collections Overview](https://www.clibs.co.uk/doc/c-craft/col/overview.html).

## License

**FREE for personal use.**  
Commercial licenses are available — please contact **sales@clibs.co.uk** for details.  
Full license terms are provided on the [C-Craft product page](https://www.clibs.co.uk/c-craft.html).

## Contributing

C-Craft is distributed and maintained by **C Libs**.  
To request features, report issues, or discuss licensing, please contact:  
**sales@clibs.co.uk**

## Acknowledgements

© 2022–2025 **C Libs** — All rights reserved.  
[https://www.clibs.co.uk](https://www.clibs.co.uk)
