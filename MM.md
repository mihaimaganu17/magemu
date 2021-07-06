# Memory Manger
-------------------

Basics:
- We need a `base` and a `size` for the amount of memory we have
- We need a page size

## Malloc
1. Find a free block of memory
    - If the amount to map is smaller than a page size, find the first page
    free and map it
    - If it is bigger, find the first n amount of pages that need to be mapped
    and map them
2. Mark it as used
    - Mark it with the proper permissions
    - You can add an identifier for that range to know what it is used for
    (in case we need to dump it. ex: name of a file, process, thread, etc)
    - Update the free memory left after the mapping has been done
3. Return its start address
    - We should know what we mapped and where it is

## Free
1. Set the memory bits to free
2. Add/Insert it back to your set of free memory ranges
3. Merge any overlapping/continuous blocks in a single range

## Design
1. We initialize a Set of free memory ranges(or one big range).
2. Each time we allocate a page, we update the Set by taking out that range
from it.
3. Each time we free a page, we insert it back in the set.
If it overlaps with any range already present, we merge them

