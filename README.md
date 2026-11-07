# mainak55512_arena.c3l
C3 binding for (https://github.com/mainak55512/arena/)[arena] allocator in C.

# Usage
```c3
module arena_example;

import std::io;
import mainak55512_arena;

alias ma = module mainak55512_arena;

fn int main(String[] args)
{
  ma::Arena *arena = ma::arena_init(20);
  defer ma::arena_free(&arena);

  double *num = ma::arena_alloc(arena,double::size);
  double *num1 = ma::arena_alloc(arena,double::size);
  double *num2 = ma::arena_alloc(arena,double::size);
  double *num3 = ma::arena_alloc(arena,double::size);
  double *num4 = ma::arena_alloc(arena,double::size);

  io::printfn("Num: %f\n",*num);

  *num = 11.22;

  *num1 = 2.345;

  io::printfn("Num: %f\n",*num);
  io::printfn("Num1: %f\n",*num1);

  ma::arena_reset(&arena);

  double *num_new = ma::arena_alloc(arena,double::size);

  io::printfn("Num_new: %f\n",*num_new);

  *num_new = 4.55;

  io::printfn("Num_new: %f\n",*num_new);
  io::printfn("Num1: %f\n",*num1);

  return 0;
}
```

