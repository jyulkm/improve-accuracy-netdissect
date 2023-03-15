---
layout: default
title: Experiment & Result
nav_order: 4
---

# Experiment & Result


\subsection{Network Dissection Intervention}
For Network Dissection Intervention, we trained VGG-16 on Places365 and experimented with conv5\_3 layer as the layer had units that captured most objects. To test the hypothesis, we performed the following steps:

\begin{enumerate}
    \item Unit Deletion Analysis: We calculated the accuracy of the VGG16 model with and without each unit in layer conv5\_3 to identify the best and worst performing units

    \item Unit Activation Analysis: We modified the output of layer conv5\_3 for the worst and best-performing units and reevaluated the accuracy of the model

    \item Weight Modification Analysis: We modified the weights of layer conv5\_3 for the worst and best-performing units and evaluated the accuracy of the model
\end{enumerate}

For both modifying unit output and weights of the layer, we experimented with dividing and multiplying constant numbers and stopped the experiment when the accuracy got below the baseline. The  results are shown in Table 1.

    \begin{table}[H]
      \caption{Network Dissect Intervention Accuracy}
      \centering
      \begin{tabular}{llll}
        \toprule
        Unit Type \& Target & Baseline & Divide/Multiply 2 & Divide/Multiply 3\\
        \midrule
        worst unit output division & 76.58\% & 76.52\% & 75.91\%\\
        worst unit weight division & 76.58\% & \textbf{76.6\%} & 76.02\%\\
        best unit weight division & 76.58\% & \textbf{76.35\%} & 75.56\%\\
        \bottomrule
      \end{tabular}
    \end{table}


\subsection{Input Gradient Regularization \& FocusedDropout}
    For FocusedDropout and Input Gradient Regularization, we trained our VGG-16 on CIFAR-100 with the following training settings:
    \begin{itemize}
    \item Batch size of 128
    \item Stochastic Gradient Descent Optimizer (Learning rate = 1e-2, momentum = 9e-1, weight decay = 5e-4)
    \item CosineAnnealingLR Scheduler (T\_max = 200)
    \item 150 Epochs
    \end{itemize}

    The classification results are shown in Table 2.

    \begin{table}[H]
      \caption{Accuracy of VGG-16 on CIFAR-100 (150 epochs)}
      \centering
      \begin{tabular}{lll}
        \toprule
        Regularization Method & Training Accuracy & Test Accuracy\\
        \midrule
        None (Baseline) & 99.97\% & 72.32\% \\
        Dropout rate 0.2 & 98.04\% & 68.16\% \\
        FocusedDropout par\_rate 0.1 & 90.71\% & \textbf{72.90\%} \\
        L2 (lambda 0.1) Input Gradient Regularization & 99.92\% & \textbf{71.67\%} \\
        \bottomrule
      \end{tabular}
    \end{table}
