# EpitopeVec: Linear Epitope Prediction Using DeepProtein Sequence Embeddings
EpitopeVec predicts linear B-cell epitopes. It takes a protein sequence (FASTA format) as input and then lists the peptides (of 20 amino acids length) that can be epitopes along with their respective predicition probability. It is based on a SVM model trained on a large set of experimentally verified epitopes and makes use of different amino acid features, k-mer features, and distributed vector representation of proteins (ProtVec).
The code for training new models and results from the EpitopVec article are available at https://github.com/hzi-bifo/epitope-prediction-paper  

## Requirements

* **```Python 3```** with the following packages:
    * **numpy 1.17.1**
    * **scipy 1.4.1**
    * **matplotlib 3.1.3**
    * **scikit-learn 0.22.1**
    * **pydpi 1.0**
    * **biopython 1.71.0**
    * **tqdm 4.15.0**
    * **gensim 2.3.0**
    
   
  If these are not installed, you can install them with ``` pip ```. 
    ```
   pip3 install -r ./requirement/requirements.txt
   ```
   
  Additionally, **pydpi 1.0** from ```pip``` might be incompatible with **Python 3**. Please install the **pydpi** package from the provided ```requirement/pydpi.tar.gz``` file.
    ```
    pip3 install ./requirement/pydpi-1.0.tar.gz
    ```
   
 * Binary file for ProtVec representation of proteins can be downloaded using the following command in the ```protvec``` directory:
 
 ```
 cd protvec
 wget http://deepbio.info/embedding_repo/sp_sequences_4mers_vec.txt
 wget http://deepbio.info/embedding_repo/sp_sequences_4mers_vec.txt.bin -O sp_sequences_4mers_vec.bin
 ```
 
   
## Usage
* Clone this repository:
  ```
  git clone https://github.com/hzi-bifo/epitope-prediction
  ```
* Run the main.py file with the following command.
  ```    
    python3 main.py -i inputfile.fasta -o outputfilename -m machine-learning-model (general OR viral)
  
    
    -i : This takes the input file with the protein sequence (in FASTA format) on which epitopes are to be predicted.
 
    -o : The name of the output directory. This will contain the list of peptides which are predicted as epitopes.
  
    -m : Machine-learning model trained on the training set as a pickle file. Use general for general predictions(default) and viral for viral prediction
  ```
## Input
  The program takes a protein sequence as input. The input file should be in **FASTA** file format and should only use the 20 aa codes.       Please put the input file in the _input_ folder or enter the full path of the inputfile. Please take a look in the _input_ folder to see an example of input fasta      file: ```example.fasta``` 
  
## Output
The output file is created in the _output_ folder with the outputname provided. It is a txt file with two columns. First column is the amino acid sequences of the predicted peptides and second column is the predicted probability score for the likelihood of that peptide being an epitope.
