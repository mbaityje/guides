# Folders operations using for loops

Imagine you have folders with regular names that contains a counter (e.g.
`Sim_1`, `Sim_2`).

Here a for loop to execute repetitive operations (e.g. running simulations)

```bash
for i in {1..2}
do
   folder="Sim_${i}"
   cd $(echo $folder)
   nohup python run.py > run.log &
   cd ..
done
```

## Specific example abcPy
```bash
for i in {1..2}
do
   folder="And_${i}_T1"
   cd $(echo $folder)
   file_py="NonConcomitant_${i}_T1.py"
   file_log="NonConcomitant_${i}_T1.log"
   nohup python $(echo $file_py) > $(echo $file_log)
   cd ..
done
```