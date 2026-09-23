# Observabilidade

Todo pipeline deve responder: está funcionando? quando rodou? quanto
demorou? quantos registros? quantos falharam? watermark? gargalo?
retries? volume de I/O?

Pilares: logs, metrics, traces.

Métricas-base: pipeline_duration_seconds, rows_processed, rows_rejected,
bytes_read, bytes_written, api_requests, api_retries, db_queries,
watermark_lag_seconds, estimated_cost.
