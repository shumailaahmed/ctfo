# ctfo

```/bin/cat $(find / -name flag.txt)
echo '<hex_string>' | awk '{ print (length($0) % 2 == 0) ? $0 : 0$0; }' | xxd -p -r > <output_file>
echo "obase=16; <decimal_number>" | BC_LINE_LENGTH=0 bc | awk '{ print (length($0) % 2 == 0) ? $0 : 0$0; }'
cat <file> | head -n <line_number> | tail -1
egrep "^([A-Za-z0-9+/]{4})*([A-Za-z0-9+/]{2}==|[A-Za-z0-9+/]{3}=|[A-Za-z0-9+/]{4})$"
tr
awk '{ printf $2 }'
ascii_char=$(printf "$(printf %x <decimal_ascii_code>)" | xxd -p -r)
echo 'hello world' | grep -oP 'hello \K(world)'
cat <json_file> | | python -m json.tool
```

