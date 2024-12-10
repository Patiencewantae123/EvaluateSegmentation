# 🩺 **EvaluateSegmentation Tool**

**EvaluateSegmentation** is a powerful tool designed to compare two volumes (a test segmentation and a ground truth segmentation) using 22 different metrics. These metrics were carefully selected based on research in medical volume segmentation to offer comprehensive evaluation.

## 📚 **Background**

The metrics used in this tool are detailed in the article **"Metrics for evaluating 3D medical image segmentation: analysis, selection, and tool"** published in _BMC Medical Imaging_. You can access the full paper [here](https://www.biomedcentral.com/1471-2342/15/29).

## 📝 **License, Copyright, and Authors**

- **Tool Name**: EvaluateSegmentation Tool
- **Developed By**: Abdel Aziz Taha ([taha@ifs.tuwien.ac.at](mailto:taha@ifs.tuwien.ac.at))
- **Copyright**: 2013, Vienna University of Technology, Institute of Software Technology and Interactive Systems
- **License**: Apache License, Version 2.0  
  You may not use this file except in compliance with the License. Full License details are available at [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0).

**Acknowledgments**: The VISCERAL project received funding from the EU FP7, contract 318068. 

## 📄 **Citing This Software**

If you use this software in your research, please cite the following papers:

- **General Tool Reference**:
  *Abdel Aziz Taha and Allan Hanbury. Metrics for evaluating 3D medical image segmentation: analysis, selection, and tool. BMC Medical Imaging, 15:29, August 2015.*  
  [PDF](http://www.biomedcentral.com/content/pdf/s12880-015-0068-x.pdf) | [BibTeX](bibtex.txt)

- **New Metric Reference (bAVD)**:
  *O. U. Aydin, A. A. Taha, A. Hilbert, A. A. Khalil, I. Galinovic, J. B. Fiebach, D. Frey, and V. I. Madai. On the usage of average Hausdorff distance for segmentation performance assessment: Hidden bias when used for ranking. European Radiology Experimental, vol. 5, 2021.*  
  [DOI: 10.1186/s41747-020-00200-2](https://doi.org/10.1186/s41747-020-00200-2)

## 📊 **Metrics Provided**

EvaluateSegmentation supports the following metrics:

### 🔗 **Similarity Measures**

1. Dice Coefficient
2. Jaccard Coefficient
3. Area under ROC Curve (one system state)
4. Cohen Kappa
5. Rand Index
6. Adjusted Rand Index
7. Interclass Correlation
8. Volumetric Similarity Coefficient
9. Mutual Information

### 📏 **Distance Measures**

10. Hausdorff Distance (optional in voxel or millimeter)
11. Average Hausdorff Distance (optional in voxel or millimeter)
12. Balanced Average Hausdorff Distance (novel metric, 2021)
13. Mahanabolis Distance
14. Variation of Information
15. Global Consistency Error
16. Coefficient of Variation
17. Probabilistic Distance

### 🔍 **Classic Measures**

18. Sensitivity (Recall, true positive rate)
19. Specificity (true negative rate)
20. Precision
21. F-Measure
22. Accuracy
23. Fallout (false positive rate)
24. True Positives (in voxel)
25. True Negatives (in voxel)
26. False Positives (in voxel)
27. False Negatives (in voxel)
28. Segmented Volume (optional in voxel or millimeter)
29. Reference Volume (optional in voxel or millimeter)

## 🖼️ **Supported Image Formats**

EvaluateSegmentation leverages the **ITK Library** and supports all 2D/3D file formats that ITK supports (e.g., `.nii`, `.mha`). The images must have the same size (number of grid points). Each image should have a single label where voxel values are either:

- `0` (background)
- A value between `0` and `1` indicating fuzzy membership/probability of the voxel belonging to the label.

## 🔧 **Usage**

### 1. **Evaluation of Volume Segmentations**

```bash
USAGE:

  EvaluateSegmentation truthPath segmentPath [-thd threshold] [-xml xmlpath] [-use all|DICE,JACRD, ....]

  where:
    truthPath: path (or URL) to the ground truth image (enclosed in quotations for URLs).
    segmentPath: path (or URL) to the image being evaluated.
    -help: Display help information.
    -thd threshold: Convert fuzzy images to binary using the given threshold.
    -xml xmlpath: Path to the XML file where results will be saved.
    -unit: Use millimeters or voxels for distances and volumes (default: voxel).
    -use metriclist: Specify metrics to be used.

    Examples:
    - EvaluateSegmentation truth.nii segment.nii --use RNDIND,HDRFDST@0.96@,FMEASR@0.5@ -xml result.xml
    - EvaluateSegmentation truth.nii segment.nii --use all --thd 0.5
```

### 2. **Evaluation of Landmark Localization**

```bash
USAGE:

  EvaluateSegmentation -loc truth_landmark_path test_landmark_path [-xml output_xml_path]

  where:
    truth_landmark_path = path (or URL) to the ground truth landmarks file.
    test_landmark_path = path (or URL) to the file containing evaluated landmarks.
    -xml output_xml_path = Path to save the result in XML format.
```

### 3. **Evaluation of Lesion Detection**

```bash
USAGE:

  EvaluateSegmentation -det truth_lesions_path test_lesions_path [-xml output_xml_path]

  where:
    truth_lesions_path = path (or URL) to the file containing ground truth lesions.
    test_lesions_path = path (or URL) to the file containing evaluated lesions.
    -xml output_xml_path = Path to save the result in XML format.
```

## ⚙️ **Builds**

- Current builds are available for **Windows** and **Ubuntu**.
- For other operating systems or updates, use the source code to create your build.

**Required Tools**:
- [ITK Library](https://itk.org/itkindex.html)
- [CMake Framework](https://cmake.org/)

---

This updated README is designed to be more engaging with icons and formatted sections for better readability.
