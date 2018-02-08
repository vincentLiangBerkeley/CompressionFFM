# CompressionFFM

The problem is to estimate a kernal function for Click Through prediction purpose: 
$\Phi(A, x) = x^TAx$ 
where $x$ is one data point and $A$ is our parameter matrix.
The function will be further breakdown by "Fields" of features which are information
added during pre-process of the data. So a data point will be:

$x = (x_1, x_2, \ldots, x_f)$  where $x_i$ is an indicator vector for field $i$.Then 
our kernal function becomes:

$\Phi(A, x) = \sum_{i\neq j} x_i^TA_{ij}x_j = \sum_{i\neq j}Tr(A_{ij}^T x_ix_j^T$

Then we will consider $x_i^Tx_j$ and assume that they share a common row and column
space across all data points and we will end up having a counting matrix:

$C = \sum_{n} x_ny_n^T$ where $x_n$ represents $x_i$ previously and $y_n$ represents
$x_j$ previously. Now inorder to incapsulate click through information we further define

$C_0 = \sum{n} I(n)x_ny_n^T$ and $C_1 = \sum{n} \hat{I}(n) x_ny_n^T$ to represent the 
counting matrix for clicks and non-clicks. Then we will try to estimate a union row and
column space for both $C_0$ and $C_1$. By the method of alternate direction desend. 
