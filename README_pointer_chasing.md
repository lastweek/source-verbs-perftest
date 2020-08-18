# For Pointer Chasing


## One-sided READ
Server (no changes at server side):
```bash
./ib_read_lat -a -F
```

Client (all changes here):
```bash
./ib_read_pc_lat -a -F 192.168.1.4 -C 
```

`nr_chase` means the extra RTT we need to take.

Be careful about the reported numbers, it might be in `ns`! Check `src/perftest_resource.c`, i've changed some.

The output looks like:
```
 #bytes #iterations    t_min[usec]    t_max[usec]  t_typical[usec]    t_avg[usec]    t_stdev[usec]   99% percentile[usec]   99.9% percentile[usec]                                                                                            
[src/read_pc_lat.c:main()] nr_chase=1                                                                                                                                                                                                         
 8       1000          3810.00        14672.00      3856.00            3900.45          512.09          4011.00                 14672.00                                                                                                      
[src/read_pc_lat.c:main()] nr_chase=2                                                                                                                                                                                                         
 8       1000          5714.00        15695.00      5773.00            5793.20          115.08          5937.00                 15695.00                                                                                                      
[src/read_pc_lat.c:main()] nr_chase=4                                                                                                                                                                                                         
 8       1000          9535.00        21410.00      9623.00            9665.68          472.87          10112.00                21410.00                                                                                                      
[src/read_pc_lat.c:main()] nr_chase=8                                                                                                                                                                                                         
 8       1000          17153.00        31740.00      17292.00          17333.48         635.50          18016.00                31740.00                                                                                                      
[src/read_pc_lat.c:main()] nr_chase=16                                                                                                                                                                                                        
 8       1000          32485.00        35505.00      32622.00          32640.52         114.45          33299.00                35505.00                                                                                                      
[src/read_pc_lat.c:main()] nr_chase=32                                                                                                                                                                                                        
 8       1000          63129.00        74479.00      63326.00          63350.42         181.36          64100.00                74479.00                                                                                                      
[src/read_pc_lat.c:main()] nr_chase=64                                                                                                                                                                                                        
 8       1000          124473.00        141662.00      124747.00               124881.18        1040.52         128707.00               141662.00                                                                                             
[src/read_pc_lat.c:main()] nr_chase=128                                                                                                                                                                                                       
 8       1000          247126.00        263518.00      247578.00               247669.07        725.41          248694.00               263518.00                                                                                             
[src/read_pc_lat.c:main()] nr_chase=256                                                                                                                                                                                                       
 8       1000          492544.00        518339.00      493314.00               493541.76        1703.03         503889.00               518339.00  
```

## Two-sided SEND
