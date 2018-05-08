### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a>Algorytmy SignedXML domyślne i SignedXMS zmieniony na SHA256

|   |   |
|---|---|
|Szczegóły|W .NET Framework 4.7 i starszych SignedXML i SignedCMS domyślne SHA1 dla niektórych operacji. Począwszy od programu .NET Framework 4.7.1 SHA256 jest domyślnie włączona dla tych operacji. Ta zmiana jest konieczne, ponieważ SHA1 przestaje być uważany za zabezpieczony.|
|Sugestia|Istnieją dwie nowe wartości przełącznika kontekstu do formantu, czy SHA1 (niebezpieczne) lub SHA256 ma być używana domyślnie:<ul><li>Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</li><li>Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms</li></ul>Dla aplikacji docelowej platformy .NET Framework 4.7.1 i nowszych wersjach, jeśli użycie SHA256 jest niepożądane, można przywrócić domyślne SHA1, dodając następującą konfigurację przełącznika do [środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji pliku config aplikacji Plik:<pre><code class="language-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true&quot; /&gt;&#13;&#10;</code></pre>Dla aplikacji przeznaczonych dla platformy .NET Framework 4.7 i wcześniejszych wersji, można włączyć w tę zmianę, dodając następujący przełącznik konfiguracji w celu [środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) sekcji w pliku konfiguracyjnym aplikacji:<pre><code class="language-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false&quot; /&gt;&#13;&#10;</code></pre>|
|Zakres|Pomocnicza|
|Wersja|4.7.1|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType></li></ul>|
