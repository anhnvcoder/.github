# .github

Repo giữ [default community health files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file)
của account `anhnvcoder`: quy ước chung, chính sách bảo mật, quy tắc ứng xử, mẫu PR và mẫu issue cho mọi repo của account.

## Bối cảnh

GitHub dùng các file mặc định ở đây cho mọi repo của account chưa có file cùng tên; file của từng repo luôn đè lên bản mặc định. Nhờ vậy quy
ước chung nằm một chỗ, mỗi repo chỉ giữ luật riêng của nó ở `AGENTS.md`.

Chỉ community health file mới thành mặc định. `LICENSE`, `Makefile`, `renovate.json` và workflow ở `.github/workflows/` của repo này chỉ áp cho
chính nó.

## Cài đặt

```sh
git clone https://github.com/anhnvcoder/.github.git
cd .github
```

Lệnh kiểm tài liệu cần Docker và `make`.

## Sử dụng

File đổi ở `main` thì mọi repo chưa có file cùng tên nhận bản mới ngay, không cần làm gì thêm. Kiểm tài liệu của repo:

```sh
make docs-check   # markdownlint-cli2 và lychee --offline trên mọi .md
make help         # liệt kê target
```

## File áp mặc định

- [`CONTRIBUTING.md`](CONTRIBUTING.md): quy ước chung của mọi repo (ngôn ngữ, tài liệu, ADR, comment, Git, repo public, phụ thuộc, chuẩn áp dụng).
- [`SECURITY.md`](SECURITY.md): cách báo lỗ hổng.
- [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md): quy tắc ứng xử, [Contributor Covenant 2.1](https://www.contributor-covenant.org/version/2/1/code_of_conduct/)
  nguyên văn tiếng Anh; báo vi phạm qua kênh riêng của `SECURITY.md`.
- [`.github/pull_request_template.md`](.github/pull_request_template.md): mẫu mô tả PR.
- [`.github/ISSUE_TEMPLATE/`](.github/ISSUE_TEMPLATE/): mẫu issue dạng
  [issue form](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/syntax-for-issue-forms): báo
  lỗi (`bug.yml`), đề xuất tính năng (`feature.yml`); `config.yml` tắt issue trống và đưa báo lỗ hổng sang chính sách bảo mật.

## Đóng góp

Quy ước chung ở [`CONTRIBUTING.md`](CONTRIBUTING.md). Mọi thay đổi vào `main` đi qua pull request có check `docs` xanh.

## Giấy phép

[Apache-2.0](LICENSE).
