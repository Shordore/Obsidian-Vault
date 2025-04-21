
find . -type f \( \
    -iname '*\(Europe\)*'   -o \
    -iname '*\(PAL\)*'      -o \
    -iname '*\(Spain\)*'    -o \
    -iname '*\(Japan\)*'    -o \
    -iname '*\(France\)*'   -o \
    -iname '*\(Pirate\)*'   -o \
    -iname '*\(Denmark\)*'  -o \
    -iname '*\(China\)*'    -o \
    -iname '*\(Beta\)*'     -o \
    -iname '*\(Germany\)*'  -o \
    -iname '*\(Proto\)*'    -o \
    -iname '*\(Canada\)*'   -o \
    -iname '*\(Demo\)*'      \
\) -delete


wget -m -np -c -e robots=off \
  -A "*\(USA\)*" \
  -R "*\(Beta\)*,*\(Demo\)*" \