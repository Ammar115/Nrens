# description

We have some netflow data for National Research and Education Networks (NRENs) across Europe. The main aim is to produce network characteristics using this data.

Data is available as network flows, captured on ingress only, aggregated to one file per 5 min interval.

Data can be viewed and processed using bzcat and nfdump Linux/Bash tools.

Data can be found under `./data`

# view file contents

You can use bash pipe with bzcat to execute nfdump and view the data. Do `man nfdump` for details.

`bzcat nfcapd.201902140000.bz2 | nfdump -N -o 'fmt:%td,%pr,%exp,%sa,%da,%sp,%dp,%nh,%nhb,%ra,%sas,%das,%in,%out,%pkt,%byt' | less`

# aggregate

Aggregate netflows:
`bzcat nfcapd.201902140000.bz2 | nfdump -a | less`

Aggregate netflows as bidirectional flows:
`bzcat nfcapd.201902140000.bz2 | nfdump -b | less`

Aggregate netflows given a field or set of fields:
`bzcat nfcapd.201902140000.bz2 | nfdump -A 'srcas,dstas' | less`

# NREN-AS mapping

NREN-AS mapping is provided in a csv under `./mappings` created using [CAIDA AS data](https://asrank.caida.org/asns/by-name).

# tasks

Writing Python code or using nfdump for tasks below is your choice. However, each task needs to be properly documented, covering what you did to solve the problem, as well as figures (matplotlib preferably) to visualise the results. I would highly recommend using nfdump tool as it already has quite a lot of things that you might need. Consider using Python as a supplement to further process the data and do the plots. If so consider using `os.system()` or similar routine.

1. Familiarise yourself with the netflow data
2. Familiarise yourself with the nfdump toolset
3. Explore NREN-AS relationship in netflow data
4. Compare NREN and non-NREN traffic in netflow data
5. Explore customer cones for NREN and non-NREN traffic (see 'customers' under 'relationship' e.g. [JANET](https://asrank.caida.org/asns/786)) -- you might have to create lists of customers per NREN AS for this

You may put analysis under `./analysis` but feel free to change the organisation of this repo as you find best.

