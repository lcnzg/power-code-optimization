# Numerical Recipes: Chapter 1.1

## Float representation
- bit S (plus or minus)
- integer E (exponent)
- binary M (mantissa)
- base b (binary = 2)
- integer constant e (bias of exponent)

S x M x b^(E-e)

## Roundoff error
- Float is not exact
- Hardware characteristic error
- Least significant bit loss
- Error at least Em
- Acumulation of error in each calculation (frequently N.Em)

## Truncation error
- Algorithm characteristic error
- Discrete approximations
- Is the difference between the real value and the calculated value

## Stability
- Control the magnitude of Roundoff errors
- Roundoff erros can grow exponentially


