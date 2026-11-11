# Project 1: NGS Sequence Data Analysis

## Title & Purpose

This Python program analyses next-generation sequencing (NGS) data from fission yeast (*S. pombe*) to identify nucleotide mutations. It investigates whether a genotoxic agent increases mutation frequency and creates specific mutation compared to untreated controls.

## How to Run the Program

Open the `.ipynb` file in Google Colab. Run the 'Setup Code' cells to download data, then execute Steps 1–5 sequentially, finishing with the 'Final analysis' cell to generate tables and statistics.

## Inputs and Outputs

Inputs are a 200-nt reference sequence (`reference.txt`) and a CSV of 6,000 aligned reads (`reads.csv`) from six samples. Outputs include annotated read dictionaries, formatted tables showing per-sample mismatch rates and substitution counts, and a statistical comparison (Welch's t-test) of top mutation positions between treatment and control groups.

## Code Design

I structured the pipeline into five modular functions (Steps 1-5). This separates validation, mutation finding, and statistical analysis, making the code easier to debug and test independently. For Step 4, I created two helper functions: `calculate_sample_stats` handles the mathematics, while `print_group_summary` handles formatting. I chose this separation of concerns over one large function to make the code cleaner and allow the statistics to be reused without printing. Additionally, I chose to return error lists in `validate_read` rather than raising exceptions. This allows the pipeline to process all 6,000 reads continuously, flagging invalid data without crashing the entire analysis.

## Testing

I tested each function with five categories of input. For `validate_read`, I tested a read with both wrong length and invalid characters to verify the error codes were returned in the correct order. For `find_mutations`, I tested a perfect match to ensure it correctly returned an empty list `[]`. For `analyse_reads`, I used a mini-dataset of six reads including valid, invalid, and lowercase inputs, then used `assert` to verify the output dictionary structure exactly matched the specification.
