# Propositional logic groceries

## Logical operator
1. `A->B`
2. `~A`

## Axiom schema
1. `p->q->p`
2. `(p->q->r)->(p->q)->(p->r)`
3. `(~p->~q)->(q->p)`

## Inference rule
1. `T |- p` and `T |- p->q` then `T |- q` (modus ponens)
2. `T |- p->q` if and only if `T+{p} |- q` (deduction theorem)

## Theorem
1. `p->(p->q)->q`
```
p, p->q |- p  # Id
p, p->q |- p->q  # Id
p, p->q |- q  # MP
p |- (p->q)->q  # DT
|- p->(p->q)->q  # DT
Q.E.D.
```

2. `p->p`
```
|- (p->(p->p)->p)->(p->p->p)->(p->p)  # A2
|- p->(p->p)->p  # A1
|- (p->p->p)->(p->p) # MP
|- p->p->p  # A1
|- p->p  # MP
Q.E.D.
```

3. `~~p->p`
```
|- ~~p->~~~~p->~~p  # A1
~~p |- ~~~~p->~~p  # DT
~~p |- (~~~~p->~~p)->(~p->~~~p)  # A3
~~p |- ~p->~~~p  # MP
~~p |- (~p->~~~p)->(~~p->p)  # A3
~~p |- ~~p->p  # MP
~~p |- p  # DT
|- ~~p->p  # DT
Q.E.D.
```

4. `p->~~p`
```
|- ~~~p->~p  # ~~p->p
|- (~~~p->~p)->(p->~~p)  # A3
|- p->~~p  # MP
Q.E.D.
```

5. `(p->q)->(q->r)->(p->r)`
```
p, p->q, q->r |- p  # Id
p, p->q, q->r |- p->q  # Id
p, p->q, q->r |- q  # MP
p, p->q, q->r |- q->r  # Id
p, p->q, q->r |- r  # MP
p->q, q->r |- p->r  # DT
p->q |- (q->r)->(p->r)  # DT
|- (p->q)->(q->r)->(p->r)  # DT
Q.E.D.
```

6. `(p->q->r)->(q->p->r)`
```
p->q->r |- p->q->r  # Id
p, p->q->r |- q->r  # DT
p, q, p->q->r |- r  # DT
q, p->q->r |- p->r  # DT
p->q->r |- q->p->r  # DT
|- (p->q->r)->(q->p->r)  # DT
Q.E.D.
```

7. `(p->q)->(~~p->q)`
```
|- (~~p->p)->(p->q)->(~~p->q)  # (p->q)->(q->r)->(p->r)
|- ~~p->p  # ~~p->p
|- (p->q)->(~~p->q)  # MP
Q.E.D.
```

8. `(p->q)->(p->~~q)`
```
|- q->~~q  # p->~~p
|- (q->~~q)->p->(q->~~q)  # A1
|- p->q->~~q  # MP
|- (p->q->~~q)->(p->q)->(p->~~q)  # A2
|- (p->q)->(p->~~q)  # MP
Q.E.D.
```

9. `(p->q)->(~q->~p)`
```
|- (~~p->p)->(p->q)->(~~p->q)  # (p->q)->(q->r)->(p->r)
|- ~~p->p  # ~~p->p
|- (p->q)->(~~p->q)  # MP
|- (~~p->q)->(q->~~q)->(~~p->~~q)  # (p->q)->(q->r)->(p->r)
~~p->q |- (q->~~q)->(~~p->~~q)  # DT
~~p->q |- q->~~q  # p->~~p
~~p->q |- ~~p->~~q  # MP
|- (~~p->q)->(~~p->~~q)  # DT
|- ((p->q)->(~~p->q))->((~~p->q)->(~~p->~~q))->((p->q)->(~~p->~~q))  # (p->q)->(q->r)->(p->r)
|- ((~~p->q)->(~~p->~~q))->((p->q)->(~~p->~~q))  # MP
|- (p->q)->(~~p->~~q)  # MP
p->q |- ~~p->~~q  # DT
p->q |- (~~p->~~q)->(~q->~p)  # A3
p->q |- ~q->~p  # MP
|- (p->q)->(~q->~p)  # DT
Q.E.D.
```

10. `(p->~q)->(q->~p)`
```
|- (p->~q)->(~~q->~p)  # (p->q)->(~q->~p)
p->~q |- ~~q->~p  # DT
p->~q |- (~~q->~p)->(q->~p)  # (p->q)->(~~p->q)
p->~q |- q->~p  # MP
|- (p->~q)->(q->~p)  # DT
Q.E.D.
```

11. `p->~q->~(p->q)`
```
p->q |- p->q  # Id
p, p->q -> q  # DT
p |- (p->q)->q  # DT
p |- ((p->q)->q)->(~q->~(p->q))  # A3
p |- ~q->~(p->q)  # MP
|- p->~q->~(p->q)  # DT
Q.E.D.
```

12. `~p->p->q`
```
|- ~p->~q->~p  # A1
~p |- ~q->~p  # DT
~p |- (~q->~p)->(p->q)  # A3
~p |- p->q  # MP
|- ~p->p->q  # DT
Q.E.D.
```

13. `~(p->q)->p`
```
|- ~p->p->q  # ~p->p->q
|- (~p->p->q)->(~(p->q)->~~p)  # (p->q)->(~q->~p)
|- ~(p->q)->~~p  # MP
|- (~(p->q)->~~p)->(~(p->q)->p)  # (p->~~q)->(p->q)
|- ~(p->q)->p  # MP
Q.E.D.
```

14. `(~p->p)->p`
```
~p->p |- ~p->p  # Id
~p->p |- ~p->p->~(~p->p)  # ~p->p->q
~p->p |- (~p->p->~(~p->p))->(~p->p)->(~p->~(~p->p))  # A1
~p->p |- (~p->p)->(~p->~(~p->p))  # MP
~p->p |- ~p->~(~p->p)  # MP
~p->p |- (~p->~(~p->p))->((~p->p)->p)  # A3
~p->p |- (~p->p)->p  # MP
~p->p |- p  # DT
|- (~p->p)->p  # DT
Q.E.D.
```

15. `(~p->q)->(~p->~q)->p`
```
~p, ~p->q, ~p->~q |- ~p  # Id
~p, ~p->q, ~p->~q |- ~p->q  # Id
~p, ~p->q, ~p->~q |- q  # MP
~p, ~p->q, ~p->~q |- ~p->~q  # Id
~p, ~p->q, ~p->~q |- ~q  # MP
~p, ~p->q, ~p->~q |- ~q->q->p  # ~p->p->q
~p, ~p->q, ~p->~q |- q->p  # MP
~p, ~p->q, ~p->~q |- p  # MP
~p->q, ~p->~q |- ~p->p  # DT
~p->q, ~p->~q |- (~p->p)->p  # (~p->p)->p
~p->q, ~p->~q |- p  # MP
~p->q |- (~p->~q)->p  # DT
|- (~p->q)->(~p->~q)->p  # DT
```

16. `(p->q)->(~p->q)->q`
```
~q, p->q, ~p->q |- ~q  # Id
~q, p->q, ~p->q |- p->q  # Id
~q, p->q, ~p->q |- (p->q)->(~q->~p)  # (p->q)->(~q->~p)
~q, p->q, ~p->q |- ~q->~p  # MP
~q, p->q, ~p->q |- ~p  # MP
~q, p->q, ~p->q |- ~p->q  # Id
~q, p->q, ~p->q |- (~p->q)->(~q->p)  # (~p->q)->(~q->p)
~q, p->q, ~p->q |- ~q->p  # MP
~q, p->q, ~p->q |- p  # MP
~q, p->q, ~p->q |- q  # MP
p->q, ~p->q |- ~q->q  # DT
p->q, ~p->q |- (~q->q)->q  # (~p->p)->p
p->q, ~p->q |- q  # MP
p->q |- (~p->q)->q  # DT
|- (p->q)->(~p->q)->q  # DT
Q.E.D.
```

17. `((p->q)->p)->p`
```
~p, (p->q)->p |- ~p->p->q  # ~p->p->q
~p, (p->q)->p |- p->q  # DT
~p, (p->q)->p |- (p->q)->p  # Id
~p, (p->q)->p |- p  # MP
(p->q)->p |- ~p->p  # DT
(p->q)->p |- (~p->p)->p  # (~p->p)->p
(p->q)->p |- p  # MP
|- ((p->q)->p)->p  # DT
Q.E.D.
```
