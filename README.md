# .github

Repo này giữ [default community health files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file)
của account `anhnvcoder`: GitHub dùng chúng cho mọi repo của account chưa có file cùng tên. File của từng repo luôn đè lên bản mặc định.

## File áp mặc định

- [`CONTRIBUTING.md`](CONTRIBUTING.md): quy ước chung của mọi repo (ngôn ngữ, tài liệu, ADR, comment, Git, repo public, phụ thuộc, chuẩn áp dụng).
- [`SECURITY.md`](SECURITY.md): cách báo lỗ hổng.
- [`.github/pull_request_template.md`](.github/pull_request_template.md): mẫu mô tả PR.

Luật làm việc riêng của mỗi repo (lệnh kiểm, an toàn cloud và database) ở `AGENTS.md` của repo đó.

## Repo của lab short-video-platform

- [`svp-backend`](https://github.com/anhnvcoder/svp-backend): service Go, `proto/`, compose, Helm chart, CI, tài liệu kiến trúc và ADR.
- [`svp-frontend`](https://github.com/anhnvcoder/svp-frontend): web Next.js và BFF.
- [`svp-gitops`](https://github.com/anhnvcoder/svp-gitops): môi trường nào chạy bản nào (Argo CD, `envs/stg`, `envs/prd`).
- [`svp-infra`](https://github.com/anhnvcoder/svp-infra): Terraform của cloud cho stg và prd.
- [`svp-labs`](https://github.com/anhnvcoder/svp-labs): bản tự làm để hiểu bên trong, dựng một lần và so với bản chuẩn.
