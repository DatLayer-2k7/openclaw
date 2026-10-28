[README.vi.md](https://github.com/user-attachments/files/33957721/README.vi.md)
# OpenClaw 🦞 — Trợ lý của bạn, trên thiết bị của bạn và trong các ứng dụng chat bạn dùng

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-banner-light.png">
    <img src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/openclaw-banner-dark.png" alt="OpenClaw — Trợ lý AI chạy trên chính thiết bị của bạn.">
  </picture>
</p>

<p align="center">
  <a href="https://github.com/openclaw/openclaw/actions/workflows/ci.yml"><img src="https://img.shields.io/github/actions/workflow/status/openclaw/openclaw/ci.yml?branch=main&style=flat-square&label=ci" alt="Trạng thái CI"></a>
  <a href="https://www.npmjs.com/package/openclaw"><img src="https://img.shields.io/npm/v/openclaw?style=flat-square&label=npm" alt="Phiên bản npm"></a>
  <a href="https://nodejs.org"><img src="https://img.shields.io/node/v/openclaw?style=flat-square" alt="Phiên bản Node.js"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="Giấy phép MIT"></a>
  <a href="https://discord.gg/clawd"><img src="https://img.shields.io/discord/1456350064065904867?label=discord&logo=discord&logoColor=white&color=5865F2&style=flat-square" alt="Cộng đồng Discord"></a>
</p>

**Ngôn ngữ:** Tiếng Việt · [English (README gốc)](README.md)

OpenClaw là một trợ lý AI mã nguồn mở chạy trên máy tính của bạn và có thể trò chuyện với bạn ngay trong những nền tảng bạn đang dùng: Discord, iMessage, Slack, Teams, Telegram, WhatsApp và hơn 20 nền tảng khác. Dự án cũng có ứng dụng riêng cho macOS, iOS, Android, Windows và Linux. Một **Gateway** có thể vận hành như trợ lý cá nhân trên laptop hoặc như hệ thống dùng chung cho nhóm; khác biệt chủ yếu nằm ở cấu hình. Xem hướng dẫn [triển khai cho nhóm](https://docs.openclaw.ai/start/teams).

## Của bạn, không có điều kiện ẩn

Trạng thái, bộ nhớ và thông tin xác thực được lưu trên phần cứng của bạn. Bạn có thể thay đổi mô hình AI và bộ công cụ vận hành tác tử (agent harness) — chẳng hạn Claude, Codex hoặc mô hình chạy cục bộ — dưới dạng plugin mà không cần thay đổi những phần còn lại.

Nội dung lời nhắc được gửi đến nhà cung cấp mô hình và các nền tảng chat mà bạn cấu hình, cùng với dữ liệu chẩn đoán nếu chính bạn bật xuất dữ liệu đó. Theo mặc định, OpenClaw chỉ liên hệ ra ngoài để kiểm tra phiên bản mỗi ngày; thống kê tính năng ẩn danh là tùy chọn tham gia. Đặt `update.checkOnStart: false` sẽ tắt cả hai. Xem [OpenClaw gửi những dữ liệu nào](https://docs.openclaw.ai/gateway/telemetry).

OpenClaw được quản lý bởi [OpenClaw Foundation](https://openclaw.org), một tổ chức độc lập thuộc diện phi lợi nhuận 501(c)(3) tại Hoa Kỳ. Dự án không có gói trả phí, dịch vụ lưu trữ do dự án vận hành hay token riêng. Lý do thiết kế — Gateway đáng tin cậy, phần thực thi không mặc nhiên đáng tin cậy và chính sách được thực thi bằng mã — được giải thích trong bài [Vì sao chọn OpenClaw](https://docs.openclaw.ai/start/why-openclaw).

**Liên kết:** [Trang chủ](https://openclaw.ai) · [Tài liệu](https://docs.openclaw.ai) · [Bắt đầu](https://docs.openclaw.ai/start/getting-started) · [Vì sao chọn OpenClaw](https://docs.openclaw.ai/start/why-openclaw) · [Câu hỏi thường gặp](https://docs.openclaw.ai/help/faq) · [Tầm nhìn dự án](VISION.md) · [DeepWiki](https://deepwiki.com/openclaw/openclaw)

## Cài đặt

Bộ cài đặt hỗ trợ macOS, Linux và Windows. Khi cần, trình cài đặt sẽ thiết lập môi trường Node.js tương thích.

**macOS / Linux / WSL2**

```bash
curl -fsSL https://openclaw.ai/install.sh | bash
```

**Windows PowerShell**

```powershell
iwr -useb https://openclaw.ai/install.ps1 | iex
```

Nếu bạn đã tự quản lý Node.js, có thể cài gói đã phát hành trực tiếp (Node.js 24.16 trở lên hoặc 26.1 trở lên; khuyến nghị Node.js 26):

```bash
npm install -g openclaw@latest --allow-scripts=openclaw
```

Lệnh trên dành cho npm 12 hoặc npm 11.16 trở lên. Với npm 11.15 trở xuống, hãy bỏ tùy chọn `--allow-scripts=openclaw`. Xem [hướng dẫn cài đặt](https://docs.openclaw.ai/install) để biết về quy trình script vòng đời, Docker, Nix và các cách triển khai khác.

## Bắt đầu nhanh

Với cài đặt mới, các script cài đặt sẽ tự khởi chạy quy trình thiết lập ban đầu. Hãy hoàn tất trình hướng dẫn được mở ra. Nếu bạn cài gói trực tiếp bằng npm, pnpm hoặc Bun, hãy chạy:

```bash
openclaw onboard --install-daemon
```

Sau khi thiết lập xong:

```bash
openclaw gateway status
openclaw dashboard
```

Quy trình thiết lập sẽ kiểm tra quyền truy cập mô hình, tạo workspace và cấu hình Gateway. Lệnh cuối cùng mở giao diện điều khiển (Control UI); hãy gửi một tin nhắn tại đó để xác nhận trợ lý hoạt động bình thường. Xem [hướng dẫn bắt đầu](https://docs.openclaw.ai/start/getting-started) để kết nối các kênh chat và khắc phục sự cố.

## Các thành phần phối hợp với nhau như thế nào?

- **[Gateway](https://docs.openclaw.ai/gateway):** lớp điều khiển cục bộ quản lý phiên làm việc, công cụ, sự kiện và kết nối đến các kênh.
- **[Control UI](https://docs.openclaw.ai/web/control-ui), CLI và [TUI](https://docs.openclaw.ai/web/tui):** các giao diện kết nối đến Gateway.
- **[Kênh chat](https://docs.openclaw.ai/channels):** đưa trợ lý đến WhatsApp, Telegram, Slack, Discord, Google Chat, Signal, iMessage và các dịch vụ nhắn tin khác.
- **[Ứng dụng đồng hành và node](https://docs.openclaw.ai/platforms):** bổ sung giọng nói, Canvas, camera, màn hình và thao tác trực tiếp trên thiết bị đối với các nền tảng được hỗ trợ.

OpenClaw tương thích với cả [nhà cung cấp mô hình](https://docs.openclaw.ai/concepts/model-providers) chạy trên dịch vụ bên ngoài lẫn mô hình cục bộ. [Công cụ](https://docs.openclaw.ai/tools), [kỹ năng (skills)](https://docs.openclaw.ai/tools/skills) và [plugin](https://docs.openclaw.ai/plugins) giúp mở rộng khả năng của trợ lý.

## Bảo mật

Hãy xem mọi tin nhắn đến là dữ liệu đầu vào chưa đáng tin cậy. Theo mặc định, những kênh hỗ trợ tin nhắn riêng (DM) sẽ yêu cầu ghép đôi với người gửi chưa biết. Bạn có thể chấp thuận yêu cầu ghép đôi bằng lệnh:

```bash
openclaw pairing approve <channel> <code>
```

Với phiên làm việc chính, các công cụ chạy trên máy chủ cho đến khi bạn cấu hình chế độ sandbox. Trước khi kết nối người dùng khác hoặc cho phép truy cập Gateway từ xa, hãy đọc [hướng dẫn bảo mật](https://docs.openclaw.ai/gateway/security), [quy trình xử lý khi Gateway bị phơi lộ ra ngoài](https://docs.openclaw.ai/gateway/security/exposure-runbook) và [hướng dẫn sandbox](https://docs.openclaw.ai/gateway/sandboxing).

## Tài liệu tham khảo

| Mục tiêu | Tài liệu |
| --- | --- |
| Cấu hình mô hình và xác thực | [Models](https://docs.openclaw.ai/concepts/models) · [Nhà cung cấp mô hình](https://docs.openclaw.ai/concepts/model-providers) |
| Kết nối dịch vụ nhắn tin | [Các kênh](https://docs.openclaw.ai/channels) |
| Thêm công cụ, kỹ năng và plugin | [Tools](https://docs.openclaw.ai/tools) · [Skills](https://docs.openclaw.ai/tools/skills) · [Plugins](https://docs.openclaw.ai/plugins) · [ClawHub](https://clawhub.ai) |
| Chạy ứng dụng và node trên thiết bị | [Nền tảng](https://docs.openclaw.ai/platforms) · [Nodes](https://docs.openclaw.ai/nodes) |
| Sử dụng CLI và lệnh trong chat | [Tham chiếu CLI](https://docs.openclaw.ai/cli) · [Lệnh slash](https://docs.openclaw.ai/tools/slash-commands) |
| Cấu hình và vận hành Gateway | [Cấu hình](https://docs.openclaw.ai/gateway/configuration) · [Kiến trúc](https://docs.openclaw.ai/concepts/architecture) · [Cập nhật](https://docs.openclaw.ai/install/updating) · [Kênh phát hành](https://docs.openclaw.ai/install/development-channels) |

## Phát triển dự án

Kho mã nguồn này sử dụng **pnpm workspace**. Không hỗ trợ chạy `npm install` tại thư mục gốc của repo.

```bash
git clone https://github.com/openclaw/openclaw.git
cd openclaw
pnpm install
pnpm build
pnpm ui:build
```

Xem [CONTRIBUTING.md](CONTRIBUTING.md) để biết quy trình đóng góp và [hướng dẫn thiết lập môi trường phát triển](https://docs.openclaw.ai/start/setup) để bắt đầu vòng lặp phát triển.

## Quản trị dự án

OpenClaw được phát triển công khai bởi [OpenClaw Foundation](https://openclaw.org), một tổ chức độc lập thuộc diện phi lợi nhuận 501(c)(3). Quỹ tuyển dụng đội ngũ nòng cốt và ký phát hành các bản phát hành chính thức. Các nhà tài trợ và đơn vị tài trợ hạ tầng hỗ trợ Quỹ nhưng không sở hữu hay chỉ đạo dự án. OpenAI là nhà tài trợ, không phải chủ sở hữu.

## Cộng đồng

Xem [CONTRIBUTING.md](CONTRIBUTING.md) để biết những người bảo trì và hướng dẫn đóng góp; các pull request có sự hỗ trợ của AI cũng được hoan nghênh.

Hãy dùng [trình chọn loại issue](https://github.com/openclaw/openclaw/issues/new/choose) để báo lỗi hoặc đề xuất tính năng, truy cập [cộng đồng OpenClaw chính thức](https://community.openclaw.ai/) để nhận hỗ trợ và gửi báo cáo lỗ hổng qua [SECURITY.md](SECURITY.md). Các khả năng mới thường nên được xây dựng thành plugin bằng [plugin SDK](https://docs.openclaw.ai/plugins/building-plugins) và chia sẻ qua [ClawHub](https://clawhub.ai).

OpenClaw được Peter Steinberger và cộng đồng xây dựng cho **Molty**, một trợ lý AI hình tôm hùm không gian. Khám phá [câu chuyện của dự án](https://docs.openclaw.ai/start/lore), [soul.md](https://soul.md), [trang cá nhân của Peter](https://steipete.me), [lịch sử sao GitHub](https://www.star-history.com/#openclaw/openclaw&type=date&legend=top-left) và tài khoản [@openclaw](https://x.com/openclaw).

Xin cảm ơn đặc biệt [Mario Zechner](https://mariozechner.at/) vì sự hỗ trợ và dự án [pi](https://github.com/earendil-works/pi), cũng như Adam Doppelt vì tên miền lobster.bot.

## Nhà tài trợ và đơn vị hỗ trợ

Quỹ nhận tài trợ từ Amazon, Lobster Computer Company, Offline Holdings, OpenAI, Red Hat và Đại học Michigan; hạ tầng được hỗ trợ bởi Blacksmith, Convex, GitHub, NVIDIA và Vercel.

<table>
  <tr>
    <td align="center"><a href="https://blacksmith.sh/"><picture><source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/sponsors/blacksmith-light.svg"><img src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/sponsors/blacksmith.svg" alt="Blacksmith" height="28"></picture></a></td>
    <td align="center"><a href="https://www.convex.dev/"><picture><source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/sponsors/convex-light.svg"><img src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/sponsors/convex.svg" alt="Convex" height="24"></picture></a></td>
    <td align="center"><a href="https://github.com/"><picture><source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/sponsors/github-light.svg"><img src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/sponsors/github.svg" alt="GitHub" height="28"></picture></a></td>
    <td align="center"><a href="https://www.nvidia.com/"><picture><source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/sponsors/nvidia.svg"><img src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/sponsors/nvidia-dark.svg" alt="NVIDIA" height="28"></picture></a></td>
    <td align="center"><a href="https://github.com/openai"><picture><source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/sponsors/openai-light.svg"><img src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/sponsors/openai.svg" alt="OpenAI" height="28"></picture></a></td>
    <td align="center"><a href="https://www.redhat.com/"><picture><source media="(prefers-color-scheme: light)" srcset="docs/assets/sponsors/redhat-light.svg"><img src="docs/assets/sponsors/redhat.svg" alt="Red Hat" height="28"></picture></a></td>
    <td align="center"><a href="https://vercel.com/"><picture><source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/sponsors/vercel-light.svg"><img src="https://raw.githubusercontent.com/openclaw/openclaw/main/docs/assets/sponsors/vercel.svg" alt="Vercel" height="24"></picture></a></td>
  </tr>
</table>

## Người đóng góp

Danh sách người đóng góp của OpenClaw được tạo tự động và khá dài, nên không sao chép toàn bộ vào bản dịch này để tránh tạo ra danh sách trùng lặp khó bảo trì. Bạn có thể xem danh sách hiện hành trong [README gốc](README.md).

## Giấy phép

Dự án sử dụng [giấy phép MIT](LICENSE), bản quyền thuộc OpenClaw Foundation. Xem [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md) để biết thông tin về mã nguồn được tích hợp hoặc điều chỉnh từ bên thứ ba.
