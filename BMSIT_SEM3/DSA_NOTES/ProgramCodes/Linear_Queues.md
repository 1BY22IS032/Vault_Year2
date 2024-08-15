# Queue

## Linear Queue

insert function: `*r == size-1`

delete function: `*f>*r = underflow`.
if underflow, reset `*f and *r`  to 0 ,-1 resp

display function: `for(int i = *f; i<=*r;i++)` for printing

main func: `*f = 0 ; *r = -1`
