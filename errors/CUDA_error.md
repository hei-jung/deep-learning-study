## CUBLAS_STATUS_INVALID_VALUE when calling `cublasSgemm`

### RuntimeError: CUDA error: CUBLAS_STATUS_INVALID_VALUE when calling `cublasSgemm( handle, opa, opb, m, n, k, &alpha, a, lda, b, ldb, &beta, c, ldc)`

[ref1](https://discuss.pytorch.org/t/runtimeerror-cuda-error-cublas-status-invalid-value-when-calling-cublassgemm-handle-opa-opb-m-n-k-alpha-a-lda-b-ldb-beta-c-ldc/124544/2)
[ref2](https://stackoverflow.com/questions/66600362/runtimeerror-cuda-error-cublas-status-execution-failed-when-calling-cublassge)

> For the peoples getting this error and ending up on this post, please know that it can also be caused if you have a mismatch between the dimension of your input tensor and the dimensions of your nn.Linear module. (ex. x.shape = (a, b) and nn.Linear(c, c, bias=False) with c not matching)

