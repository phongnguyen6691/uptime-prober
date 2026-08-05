# uptime-prober

External prober cho `status.phongnguyen.dev` — chạy từ GitHub Actions (ngoài host),
bắt lớp sự cố mà mọi alert trên host đều mù: host chết hẳn / mất inbound.
Alert qua Telegram OPS bot (secrets `TG_BOT`, `TG_CHAT`). Chi tiết division-of-labor:
`ai-workflows/docs/ops-alerts.md` trên host.

- `probe.yml` — mỗi 5 phút (GH jitter thực tế 5–15'), 2 lần thử, alert khi chuyển trạng thái
  (state = conclusion của run trước). Run đỏ = target down (đúng chủ đích).
- `keepalive.yml` — commit rỗng mỗi tháng, chống GitHub tự tắt schedule sau 60 ngày im lặng.
