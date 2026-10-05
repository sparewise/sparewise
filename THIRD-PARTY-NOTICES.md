# Third-party notices

Sparewise is proprietary software (see LICENSE). It includes the components below, each
used under its own license. Their licenses apply to those components only. Versions are those the
current build uses (read from each package's metadata).

| Component | Version | License | Project |
|---|---|---|---|
| WPF-UI (and WPF-UI.Abstractions) | 4.3.0 | MIT | https://github.com/lepoco/wpfui |
| CommunityToolkit.Mvvm | 8.4.2 | MIT | https://github.com/CommunityToolkit/dotnet |
| Velopack | 1.2.158 | MIT | https://github.com/velopack/velopack |
| Microsoft.Data.Sqlite (and .Core) | 10.0.12 | MIT | https://github.com/dotnet/efcore |
| System.Management | 10.0.12 | MIT | https://github.com/dotnet/runtime |
| SQLitePCLRaw (bundle_e_sqlite3, core, lib.e_sqlite3, provider.e_sqlite3) | 2.1.12 | Apache-2.0 | https://github.com/ericsink/SQLitePCL.raw |
| SQLite | (bundled by SQLitePCLRaw) | Public domain | https://www.sqlite.org/copyright.html |
| .NET runtime | 10 | MIT | https://github.com/dotnet/runtime |

Test-only components (not shipped): xUnit (Apache-2.0), FlaUI (MIT), coverlet (MIT), Microsoft.NET.Test.Sdk (MIT).

## License texts

**MIT License** (WPF-UI, CommunityToolkit.Mvvm, Velopack, Microsoft.Data.Sqlite, System.Management, .NET):
the copyright notice of each project and this permission notice must be included in copies:

> Permission is hereby granted, free of charge, to any person obtaining a copy of this software and
> associated documentation files (the "Software"), to deal in the Software without restriction,
> including without limitation the rights to use, copy, modify, merge, publish, distribute,
> sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is
> furnished to do so, subject to the following conditions: The above copyright notice and this
> permission notice shall be included in all copies or substantial portions of the Software.
> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED.

**Apache License 2.0** (SQLitePCLRaw): https://www.apache.org/licenses/LICENSE-2.0 — a copy of the
license and any NOTICE file of the component must be provided with distributions.

Before a release, the packaging step should copy each component's own LICENSE file into the
package (Velopack bundle, portable zip, npm vendor folder).
