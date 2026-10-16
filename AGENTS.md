<!-- LOVABLE:BEGIN -->
> [!IMPORTANT]
> This project is connected to [Lovable](https://lovable.dev). Avoid rewriting
> published git history — force pushing, or rebasing/amending/squashing commits
> that are already pushed — as it rewrites history on Lovable's side and the
> user will likely lose their project history.
>
> Commits you push to the connected branch sync back to Lovable and show up in
> the editor, so keep the branch in a working state.
<!-- LOVABLE:END -->

## Application architecture
- Use TanStack file routes and a services index plus Outlet parent so service detail pages render independently.
- Keep shared Ukrainian content, types and quote logic in one client-safe data module to support future localization.
- Read public content through a public server function and route query loaders; call protected admin functions only after client session hydration to preserve public SSR.
- Verify the separate user_roles table on every admin action and enforce matching RLS policies; account creation never grants admin privileges.
- Store request photos in private storage with temporary admin-only signed links; public portfolio images are compressed by the owner editor and stored with content because public buckets are disallowed.
- Keep styles and colors in global semantic design tokens so all routes follow the same visual system.
- Export source without environment files, dependencies, generated route tree or build output; this application requires an SSR-capable hosting runtime and a separately configured backend.
