# Đóng góp

Quy ước chung của mọi repo thuộc account `anhnvcoder`. Luật riêng của mỗi repo (lệnh kiểm, an toàn cloud và database, bố cục) ở `AGENTS.md`
của repo đó; khi hai bên khác nhau, file của repo thắng.

## 1. Ngôn ngữ

- Mọi thứ trong code viết tiếng Anh (thông lệ chung để code đọc được với mọi người): comment, log, tên test, error message, `description` của biến, file cấu hình, `*.example`.
- Ngôn ngữ của tài liệu (`.md`) do mỗi repo chọn, ghi trong `AGENTS.md` hay `README.md` của repo đó.

## 2. Tài liệu

- **Cấu trúc:** theo [Diátaxis](https://diataxis.fr): mỗi tài liệu thuộc một loại (tutorial, how-to, reference, explanation).
- **Cửa vào:** `README.md` theo [standard-readme](https://github.com/RichardLitt/standard-readme).
- **Văn phong:** theo [Google developer documentation style guide](https://developers.google.com/style): câu ngắn, chủ động, thuật ngữ nhất quán.
- **Timeless:** tài liệu và code hiện trạng nói thứ đó là gì và làm gì. Không ngày đổi, không nhãn tiến độ. Lịch sử chỉ nằm ở ADR,
  CHANGELOG theo [Keep a Changelog](https://keepachangelog.com), postmortem và mô tả PR. Mốc "tính đến" có nguồn cho dữ kiện bên ngoài thì được.
  Bước chuyển đổi chạy một lần (chuyển zone, đổi tên, đổi state) nằm ở PR, ADR hay runbook riêng trong lúc chạy; chạy xong thì gỡ khỏi README
  và runbook, để chúng chỉ tả hệ thống như hiện có.
- **Một nguồn sự thật:** không ghi cứng số lượng, danh sách hay version mà code hoặc file khác đã giữ; trỏ tới nguồn đó (ví dụ "mọi repo trong
  danh sách của `repositories.tf`" thay vì "sáu repo"), để thêm hay bớt một mục không làm tài liệu sai.

## 3. ADR

- Theo [MADR 4](https://adr.github.io/madr/) và ý của Michael Nygard: bối cảnh, phương án đã cân nhắc, quyết định, hệ quả.
- ADR là nhật ký lý do, khoảng 150 dòng; chi tiết dài để ở `docs/` hay runbook rồi link sang.
- ADR đã chấp nhận không sửa quyết định. Đổi ý thì viết ADR mới và đánh dấu ADR cũ là "Bị thay bởi".

## 4. Comment trong code

Comment tự đủ nghĩa: nói lý do ngay tại chỗ. Không nhắc ADR, nhãn tiến độ hay ticket, vì số mục đổi hay ADR bị thay thì tham chiếu thành sai.

- **Nói vì sao, không kể lại code:** giải thích lý do (*why*), không kể lại hay diễn giải điều code đã tự thể hiện (*what*), không liệt kê bước hay giải thích cú pháp theo [Go Doc Comments](https://go.dev/doc/comment) và [Google Shell Style Guide](https://google.github.io/styleguide/shellguide.html#comments) (mục Comments).
- **Chỉ đặt ở chỗ code không tự nói:** chỉ viết comment ở nơi đọc code không tự hiểu được như luật bảo mật ([GitHub Actions security hardening](https://docs.github.com/en/actions/security-for-github-actions/security-guides/security-hardening-for-github-actions)), lỗi hoặc giới hạn của nền tảng và công cụ, ràng buộc lạ, guard bắt buộc phải giữ, hoặc ngoại lệ có chủ đích.
- **Giới hạn độ dài (của dự án):** áp cho comment thường ở mọi ngôn ngữ: mỗi khối comment liền nhau tối đa 4 dòng (riêng khối đầu file của workflow và action dưới `.github/` tối đa 8 dòng), mỗi dòng tối đa 120 ký tự.
- **Doc comment theo chuẩn của ngôn ngữ:** không chịu giới hạn trên. Go theo [Go Doc Comments](https://go.dev/doc/comment) (doc của package, kiểu, hàm được nhiều đoạn), TypeScript theo [TSDoc](https://tsdoc.org) (`/** */`), proto theo comment của phần tử trong [Protocol Buffers style guide](https://protobuf.dev/programming-guides/style/), Helm theo khối `# --` của [helm-docs](https://github.com/norwoodj/helm-docs). Mô tả biến và output của Terraform nằm ở `description` (dữ liệu mà [terraform-docs](https://terraform-docs.io) đọc), không ở comment. Doc comment là hợp đồng của API: không chứa lịch sử, so sánh phương án hay quy trình ngoài file.
- **Giải thích dài vào tài liệu:** lý do thiết kế dài (so sánh phương án, bối cảnh lịch sử, kiến trúc luồng) thuộc loại tài liệu explanation theo [Diátaxis](https://diataxis.fr) trong file `.md` của repo; comment trong code chỉ giữ tối đa một dòng trỏ tới file đó, viết bằng cú pháp comment của file (`# Design notes: <đường dẫn từ gốc repo>.`, `// Design notes: <đường dẫn từ gốc repo>.`).
- **Chỉ dẫn công cụ không đổi:** comment chỉ dẫn cho công cụ (directive như `# shellcheck`, `# renovate:`, `# zizmor:`, `//go:embed`, `//nolint:<linter> // <lý do>`, `// eslint-disable-next-line`, `// @ts-expect-error`, `#trivy:ignore`, `-- name:` của sqlc) và comment tag phiên bản sau `uses: ...@<sha>` giữ nguyên đúng cú pháp theo chuẩn của từng công cụ như [ShellCheck](https://www.shellcheck.net) và [Renovate](https://docs.renovatebot.com).

Chuẩn theo ngôn ngữ:

| Ngôn ngữ | Chuẩn |
| --- | --- |
| Go | [Go Doc Comments](https://go.dev/doc/comment), [Effective Go](https://go.dev/doc/effective_go), [Google Go Style Guide](https://google.github.io/styleguide/go) |
| Shell | [Google Shell Style Guide](https://google.github.io/styleguide/shellguide.html) và [ShellCheck](https://www.shellcheck.net); script dài thì viết bằng Go |
| TypeScript | [TSDoc](https://tsdoc.org) |
| Protobuf | [Protocol Buffers style guide](https://protobuf.dev/programming-guides/style/) |
| Terraform | [HashiCorp Terraform style guide](https://developer.hashicorp.com/terraform/language/style) và [terraform-docs](https://terraform-docs.io) |
| Helm | [Helm chart best practices](https://helm.sh/docs/chart_best_practices/) và [helm-docs](https://github.com/norwoodj/helm-docs) |

## 5. Git

- Commit theo [Conventional Commits](https://www.conventionalcommits.org); mô tả viết tiếng Việt.
- Mọi thay đổi vào `main` đi qua PR có check bắt buộc xanh, squash merge. Không force push; hoàn tác bằng PR revert.
- **Tiêu đề PR theo Conventional Commits**, vì commit squash lấy tiêu đề và mô tả của PR: tiêu đề PR chính là thông điệp commit trên `main`.
- **Lịch sử `main` tuyến tính:** mỗi commit là một PR, nên hoàn tác một thay đổi là revert đúng một commit. PR revert giữ tiêu đề
  `Revert "…"` do GitHub đặt, không viết lại theo Conventional Commits.

## 6. Repo public

Mọi thứ đã commit ai cũng đọc được. Không commit secret, `.env`, state, plan, account ID, IP, email, tên miền thật. Giá trị cá nhân đi qua
file `*.example` và file gitignore.

## 7. Phụ thuộc và công cụ

- Ghim chính xác: version, digest `@sha256:` của image, SHA của action. [Renovate](https://docs.renovatebot.com) nâng bản.
- Thêm công cụ hay thư viện phải có lý do; công cụ đổi thì viết ADR.

## 8. Chuẩn áp dụng

| Mảng | Chuẩn |
| --- | --- |
| Cấu trúc tài liệu | [Diátaxis](https://diataxis.fr) |
| Cửa vào | [standard-readme](https://github.com/RichardLitt/standard-readme) |
| Văn phong | [Google developer documentation style guide](https://developers.google.com/style) |
| Kiểm tài liệu | [Docs as code](https://www.writethedocs.org/guide/docs-as-code/): [markdownlint-cli2](https://github.com/DavidAnson/markdownlint-cli2), [lychee](https://lychee.cli.rs), `make docs-check` ở mỗi repo |
| Lịch sử thay đổi | [Keep a Changelog](https://keepachangelog.com) |
| Quyết định kiến trúc | [MADR 4](https://adr.github.io/madr/) |
| Commit | [Conventional Commits](https://www.conventionalcommits.org) |
| Comment Go | [Go Doc Comments](https://go.dev/doc/comment), [Effective Go](https://go.dev/doc/effective_go), [Google Go Style Guide](https://google.github.io/styleguide/go) |
| Shell | [Google Shell Style Guide](https://google.github.io/styleguide/shellguide.html), [ShellCheck](https://www.shellcheck.net) |
| TypeScript | [TSDoc](https://tsdoc.org) |
| Terraform | [HashiCorp Terraform style guide](https://developer.hashicorp.com/terraform/language/style), [terraform-docs](https://terraform-docs.io) |
| Helm | [Helm chart best practices](https://helm.sh/docs/chart_best_practices/), [helm-docs](https://github.com/norwoodj/helm-docs) |
| Tệp cộng đồng | [GitHub community health files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file) |
| Báo lỗ hổng | [Private vulnerability reporting](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability) |
