echo -e "aaaaaaaaaaaaaaaaaa" | ./fs2tar -t nilfs2 -p nilfs2_temp.bin out.tar

make CC=/home/konrad/dev/AFLplusplus/afl-clang-fast -C tools/lkl -j72

rm ./tools/lkl/lib/lkl.o

~/dev/AFLplusplus/afl-fuzz -i in -o out -t 5000 -m 10000 -- ./fs2tar -t nilfs2 -p nilfs2_temp.bin out.tar                
