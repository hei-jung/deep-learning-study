## CUBLAS_STATUS_INVALID_VALUE when calling `cublasSgemm`

### RuntimeError: CUDA error: CUBLAS_STATUS_INVALID_VALUE when calling `cublasSgemm( handle, opa, opb, m, n, k, &alpha, a, lda, b, ldb, &beta, c, ldc)`

[ref1](https://discuss.pytorch.org/t/runtimeerror-cuda-error-cublas-status-invalid-value-when-calling-cublassgemm-handle-opa-opb-m-n-k-alpha-a-lda-b-ldb-beta-c-ldc/124544/2)
[ref2](https://stackoverflow.com/questions/66600362/runtimeerror-cuda-error-cublas-status-execution-failed-when-calling-cublassge)

> For the peoples getting this error and ending up on this post, please know that it can also be caused if you have a mismatch between the dimension of your input tensor and the dimensions of your nn.Linear module. (ex. x.shape = (a, b) and nn.Linear(c, c, bias=False) with c not matching) (ref1)


## `device-side assert triggered` error

### RuntimeError: CUDA error: device-side assert triggered CUDA kernel errors might be asynchronously reported at some other API call,so the stacktrace below might be incorrect. For debugging consider passing CUDA_LAUNCH_BLOCKING=1.

[ref1](https://stackoverflow.com/questions/68166721/cuda-error-device-side-assert-triggered-on-colab)
[ref2](https://brstar96.github.io/shoveling/device_error_summary/)
[ref3](https://ndb796.tistory.com/509)
[ref4](https://programmerah.com/solved-runtimeerror-cuda-error-device-side-assert-triggered-30474/)

> 실제로는 입출력 차원(dimension)을 제대로 맞추지 않아서 발생하는 경우가 많다. 필자의 경우 ① 실제 데이터셋과는 다르게 출력(output) 차원의 크기를 설정했을 때 그리고 ② 실제 데이터셋과는 다르게 입력(output) 차원의 크기를 설정했을 때 (ref3)

> Some people say that the reason for this problem is that there are tags exceeding the number of categories in the training data when doing the classification task. For example: if you set up a total of 8 classes, but there is 9 in the tag in the training data, this error will be reported. So here’s the problem. There’s a trap. If the tag in the training data contains 0, the above error will also be reported. This is very weird. Generally, we start counting from 0, but in Python, the category labels below 0 have to report an error. So if the category label starts from 0, add 1 to all category labels. (ref4)


## CUBLAS_STATUS_NOT_INITIALIZED when calling `cublasCreate(handle)`

### RuntimeError: CUDA error: CUBLAS_STATUS_NOT_INITIALIZED when calling `cublasCreate(handle)`

[ref1](https://discuss.pytorch.org/t/cuda-error-cublas-status-not-initialized-when-calling-cublascreate-handle/125450)

> This error might be raised, if you are running out of memory and cublas fails to create the handle, so try to reduce the memory usage e.g. via a smaller batch size. (ref1)


## CUDA error: CUBLAS_STATUS_ALLOC_FAILED when calling `cublasCreate(handle)`

### RuntimeError: CUDA error: CUBLAS_STATUS_ALLOC_FAILED when calling `cublasCreate(handle)`

[ref1](https://developers-shack.tistory.com/5)
[ref2](https://discuss.pytorch.org/t/runtimeerror-cuda-error-cublas-status-alloc-failed-when-calling-cublascreate-handle-while-running-fine-on-the-cpu/108740)
[ref3](https://stackoverflow.com/questions/63930934/cuda-error-cublas-status-alloc-failed-when-running-loss-backward)


=> classification problem을 위한 model을 만들 때는 마지막 FC layer의 output channel 개수가 무조건 class 수와 같아야 한다.<br>
위의 에러들은 전부 그걸 안 지켜서 발생한 에러.

