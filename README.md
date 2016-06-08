# fa4tr.pl
merge.plで生成されたORFのmultiple fasta fileに対してCOG DB, RefSeq DBでBLAST検索を行った結果から、ヒットしなかったORFのmultiple fasta fileを出力するスクリプト。実行にBioPerlが必要であるため、base imageとしてyookuda/bioperlを使用する。

## Usage
```usage
docker run \
    -v data_dir_path:/data \
    --rm \
    yookuda/fa4tr \
    perl /scripts/fa4tr.pl \
        --fa /data/<同定されたORFのmultiple fasta file> \
        --cog /data/<COG DBでのBLAST検索結果ファイル> \
        --ref /data/<RefSeq DBでのBLAST検索結果ファイル> \
        --out /data/<COG, RefSeqでヒットしなかったOFRのmultiple fasta file>
```
- BLAST検索結果ファイルは-outfmt "0" オプションで出力したものを使用する。
