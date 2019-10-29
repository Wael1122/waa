This is the format neofetch uses for it's ascii art files and the format you should follow when adding ascii art to onefetch.

#### Here's an example:

```sh
# resources/racket.ascii
{0}            {2}.:--::////::--.`
{0}        {1}`/yNMMNho{2}////////////:.
{0}      {1}`+NMMMMMMMMmy{2}/////////////:`
{0}    `-:::{1}ohNMMMMMMMNy{2}/////////////:`
{0}   .::::::::{1}odMMMMMMMNy{2}/////////////-
{0}  -:::::::::::{1}/hMMMMMMMmo{2}////////////-
{0} .::::::::::::::{1}oMMMMMMMMh{2}////////////-
{0}`:::::::::::::{1}/dMMMMMMMMMMNo{2}///////////`
{0}-::::::::::::{1}sMMMMMMmMMMMMMMy{2}//////////-
{0}-::::::::::{1}/dMMMMMMs{0}:{1}+NMMMMMMd{2}/////////:
{0}-:::::::::{1}+NMMMMMm/{0}:::{1}/dMMMMMMm+{2}///////:
{0}-::::::::{1}sMMMMMMh{0}:::::::{1}dMMMMMMm+{2}//////-
{0}`:::::::{1}sMMMMMMy{0}:::::::::{1}dMMMMMMm+{2}/////`
{0} .:::::{1}sMMMMMMs{0}:::::::::::{1}mMMMMMMd{2}////-
{0}  -:::{1}sMMMMMMy{0}::::::::::::{1}/NMMMMMMh{2}//-
{0}   .:{1}+MMMMMMd{0}::::::::::::::{1}oMMMMMMMo{2}-
{0}    {1}`yMMMMMN/{0}:::::::::::::::{1}hMMMMMh.
{0}      {1}-yMMMo{0}::::::::::::::::{1}/MMMy-
{0}        {1}`/s{0}::::::::::::::::::{1}o/`
{0}            ``.---::::---..`
```

#### Features:

- You can use `{0}` to `{X}`to color the ascii, with X > 0.
- You can pass the flag `-c, --colors 2 5 ...` to set your own colors.
    - Look at the visual marker to know the color order.
