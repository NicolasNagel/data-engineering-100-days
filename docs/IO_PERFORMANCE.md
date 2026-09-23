# I/O e Performance

Perguntar sempre: quantos bytes entram/saem? de onde para onde? cabe em
memória? materializa tudo? lê colunas desnecessárias? pode filtrar
antes? há compressão? quantas operações de rede/disco?

Métricas: bytes_read, bytes_written, rows_read, rows_written,
elapsed_seconds, throughput_mb_s, peak_memory_mb.

Laboratórios: CSV vs Parquet; leitura total vs chunks; Pandas vs Polars
lazy; DuckDB; pruning e pushdown.
