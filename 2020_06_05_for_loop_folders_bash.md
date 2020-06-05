# Folders operations using for loops

Imagine you have folders with regular names that contains a counter (e.g.
`Sim_1`, `Sim_2`).

Here a for loop to execute repetitive operations (e.g. running simulations)

```bash
for i in {1..2}
do
   folder_name="Sim_${i}"
   cd $(echo $folder)
   nohup python run.py > run.log &
   cd ..
done
```