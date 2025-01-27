# extractonlymissenseSNPs

## Overview
This script is designed for extracting shared polymorphisms from multiple VCF files using **BCFTools** and basic Bash commands. After extracting the polymorphisms, you can count specific variants of interest, such as missense SNPs, using simple `grep -c` commands.

---

## Features
- Extracts SNPs and shared polymorphisms from VCF files.
- Allows counting of specific polymorphism types (e.g., missense variants).
- Simple and efficient workflow utilizing **BCFTools**.

---

## Getting Started
Follow these instructions to extract and count polymorphisms of interest from your VCF files.

### System Requirements
This script has been tested on the following system:
- **Operating System**: macOS X  
  - Product Version: 10.14.4  
  - Build Version: 18E226  
- **BCFTools**: Version 1.9 (with HTSlib 1.9)

### Prerequisites
Ensure that **BCFTools** is installed on your system. If not, you can install it by following the steps below.

---

## Usage

### Step 1: Set Your Working Directory
Change the current working directory to the location where you want to store or process your VCF files:
```bash
cd /path/to/your/working/directory
```

### Step 2: Install BCFTools
If BCFTools is not already installed, you can install it using a package manager like **Homebrew**:
```bash
brew install bcftools
```
Alternatively, you can download and build BCFTools from the source:
```bash
git clone https://github.com/samtools/bcftools.git
cd bcftools
make
```

---

## Next Steps
Once BCFTools is installed and your working directory is set:
1. Extract the polymorphisms of interest using BCFTools commands.
2. Count specific polymorphisms, such as missense variants, with `grep -c`.

Example command to extract only missense SNPs:
```bash
bcftools view -i 'TYPE="snp" && INFO/ANN ~ "missense_variant"' input.vcf > output_missense_snps.vcf
```

Count the number of missense SNPs in the VCF:
```bash
grep -c "missense_variant" output_missense_snps.vcf
```

---

## Additional Notes
- Ensure that the input VCF files are properly indexed with a `.tbi` file using `bcftools index`.
- The script can be customized to filter for other variant classes based on your research needs.

For more information on BCFTools commands and filters, refer to the [official BCFTools documentation](http://samtools.github.io/bcftools/).

---
