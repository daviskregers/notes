# Support Vector Machines

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/18-support-vector-machines.ipynb

- Works well for classifying higher-dimensional data (lots of features)
- Finds higher dimensional support vecors accross which to divide the data (mathematically, these support vectors define hyperplanes.)
- Uses something called kernel trick to represent data in higher-dimensional spaces to find hyperplanes that might not be apparent in lower dimensions.

## Support Vector Classification

- In practice you'll use something called SVC to classify data using SVM.
- You can use different "kernels" with SVC. Some will work better than others for a given data set.

![svc](svc.png)
