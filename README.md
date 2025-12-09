# MOEE
## Mixture of Embedding Experts for Open Knowledge Graphs

Source code for our Neurocomputing paper

### Dependencies:

* Compatible with Pytorch 1.8 and Python 3.8.

### Dataset:
* ReVerb45k, ReVerb20K are included with the repository present in the `Data` directory.
* Both datasets contain the following files:

  ```shell
  ent2id.txt: all noun phrases and corresponding ids, one per line. The first line is the number of noun phrases.

  rel2id.txt: all relation phrases and corresponding ids, one per line. The first line is the number of relations.

  train_trip.txt: training file, the first line is the number of triples for training. Then the following lines are all in the format ***(s,r,o)*** which indicates there is a relation ***rel*** between ***s*** and ***o*** .
  
  test_trip.txt: testing file, the first line is the number of triples for testing. Then the following lines are all in the format ***(s,r,o)*** .

  valid_trip.txt: validating file, the first line is the number of triples for validating. Then the following lines are all in the format ***(s,r,o)*** .
  
  gold_npclust.txt: The ground truth noun phrase canonicalization information. This information is used during evaluations. Each line corresponds to the canonicalization information of a noun phrase in the following format ***(NP_id, no. of canonical NPs, list ids of canonical NPs)*** .
  
  rel2type.txt: relation categories.
  ```

  
### Code:

* Pretrain:
  ```shell
  cd code/MOEE_Pretrain
  CUDA_VISIBLE_DEVICES=1 python main.py -dataset ReVerb45K -lr 0.00005 -neg_samples 50 -rel_neg_samples 10 -n_epochs 500 -early_stop 10 -batch_size 512
  ```
* Finetune:
  ```shell
  cd code/MOEE_Finetune
  CUDA_VISIBLE_DEVICES=1 python main.py -dataset ReVerb45K -lr 0.00005 -n_epochs 500 -early_stop 50 --PT True --kge MOE --top_k 2 --headcatrel True --num_experts 4
  ```

### Citation
Please cite our paper if you use this code in your work: Mixture of Embedding Experts for Open Knowledge Graphs

        @article{li2025moee, 
        title={Mixture of Embedding Experts for Open Knowledge Graphs}, 
        author={}, 
        journal={Neurocomputing}, 
        year={2025} }


For any clarification, comments, or suggestions please create an issue or contact feiwangyuzhou@sdu.edu.cn
