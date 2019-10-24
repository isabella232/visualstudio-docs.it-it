---
title: Colorazione della sintassi in un servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19561363affada05154e15142bd32a30a5d051d0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722839"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Colorazione della sintassi in un servizio di linguaggio legacy
La colorazione della sintassi è una funzionalità che determina la visualizzazione di elementi diversi di un linguaggio di programmazione in un file di origine con colori e stili diversi. Per supportare questa funzionalità, è necessario fornire un parser o uno scanner in grado di identificare i tipi di elementi o token lessicali nel file. Molti linguaggi distinguono le parole chiave, i delimitatori, ad esempio le parentesi o le parentesi graffe, e i commenti per colorarli in modi diversi.

 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni, vedere [estensione dei servizi di editor e di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.

## <a name="implementation"></a>Implementazione
 Per supportare la colorazione, il Framework di pacchetto gestito (MPF) include la classe <xref:Microsoft.VisualStudio.Package.Colorizer>, che implementa l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. Questa classe interagisce con un <xref:Microsoft.VisualStudio.Package.IScanner> per determinare il token e i colori. Per altre informazioni sugli scanner, vedere [parser e scanner del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). La classe <xref:Microsoft.VisualStudio.Package.Colorizer> contrassegna quindi ogni carattere del token con le informazioni sul colore e restituisce tali informazioni all'editor che Visualizza il file di origine.

 Le informazioni sul colore restituite all'editor sono costituite da un indice in un elenco di elementi colorabili. Ogni elemento colorabile specifica un valore di colore e un set di attributi del tipo di carattere, ad esempio grassetto o barrato. L'editor fornisce un set di elementi colorabili predefiniti che possono essere utilizzati dal servizio di linguaggio. È sufficiente specificare l'indice dei colori appropriato per ogni tipo di token. Tuttavia, è possibile fornire un set di elementi colorabili personalizzati e gli indici forniti per i token e fare riferimento al proprio elenco di elementi colorabili anziché all'elenco predefinito. È anche necessario impostare la voce del registro di sistema `RequestStockColors` su 0 (oppure non specificare la voce `RequestStockColors`) per supportare i colori personalizzati. È possibile impostare questa voce del registro di sistema con un parametro denominato per il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attributo definito dall'utente. Per ulteriori informazioni sulla registrazione di un servizio di linguaggio e sull'impostazione delle relative opzioni, vedere la pagina relativa alla [registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md).

## <a name="custom-colorable-items"></a>Elementi colorabili personalizzati
 Per fornire elementi colorabili personalizzati, è necessario eseguire l'override del metodo <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> e <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> nella classe <xref:Microsoft.VisualStudio.Package.LanguageService>. Il primo metodo restituisce il numero di elementi colorabili personalizzati supportati dal servizio di linguaggio e il secondo ottiene l'elemento colorabile personalizzato in base all'indice. Si crea l'elenco predefinito di elementi colorabili personalizzati. Nel costruttore del servizio di linguaggio è sufficiente specificare ogni elemento colorabile con un nome. Visual Studio gestisce automaticamente il caso in cui l'utente seleziona un set di elementi colorabili diverso. Questo nome viene visualizzato nella pagina delle proprietà **tipi di carattere e colori** della finestra di dialogo **Opzioni** , disponibile nel menu **strumenti** di Visual Studio, e questo nome determina il colore di cui un utente ha eseguito l'override. Le scelte dell'utente vengono archiviate in una cache nel registro di sistema e accessibili dal nome del colore. La pagina delle proprietà **tipi di carattere e colori** elenca tutti i nomi di colore in ordine alfabetico, in modo che sia possibile raggruppare i colori personalizzati precedere ogni nome di colore con il nome della lingua. ad esempio, "**TestLanguage-comment**" e "**TestLanguage-keyword**". In alternativa, è possibile raggruppare gli elementi colorabili per tipo, "**Comment (TestLanguage)** " e "**keyword (TestLanguage)** ". Il raggruppamento in base al nome del linguaggio è preferibile.

> [!CAUTION]
> È consigliabile includere il nome della lingua nel nome dell'elemento colorabile per evitare conflitti con i nomi degli elementi colorabili esistenti.

> [!NOTE]
> Se si modifica il nome di uno dei colori durante lo sviluppo, è necessario reimpostare la cache creata da Visual Studio la prima volta che si accede ai colori. A tale scopo, è possibile eseguire il comando **Reimposta l'hive sperimentale** dal menu programma di Visual Studio SDK.

 Si noti che non viene mai fatto riferimento al primo elemento dell'elenco di elementi colorabili. Visual Studio fornisce sempre gli attributi e i colori del testo predefiniti per l'elemento. Il modo più semplice per gestire questo problema consiste nel fornire un elemento colorabile segnaposto come primo elemento.

### <a name="high-color-colorable-items"></a>Elementi colorabili ad alta colorazione
 Gli elementi colorabili possono inoltre supportare i valori di colore a 24 bit o alto tramite l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>. La classe <xref:Microsoft.VisualStudio.Package.ColorableItem> MPF supporta l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> e i colori a 24 bit vengono specificati nel costruttore insieme ai colori normali. Per ulteriori dettagli, vedere la classe <xref:Microsoft.VisualStudio.Package.ColorableItem>. Nell'esempio seguente viene illustrato come impostare i colori a 24 bit per le parole chiave e i commenti. I colori a 24 bit vengono utilizzati quando il colore a 24 bit è supportato sul desktop dell'utente. in caso contrario, vengono utilizzati i normali colori del testo.

 Tenere presente che si tratta dei colori predefiniti per il linguaggio in uso. l'utente può modificare questi colori in base a quanto desiderato.

### <a name="example"></a>Esempio
 Questo esempio illustra un modo per dichiarare e popolare una matrice di elementi colorabili personalizzati usando la classe <xref:Microsoft.VisualStudio.Package.ColorableItem>. Questo esempio Mostra come impostare la parola chiave e i colori dei commenti usando i colori a 24 bit.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private ColorableItem[] m_colorableItems;

        TestLanguageService() : base()
        {
            m_colorableItems = new ColorableItem[] {
                new ColorableItem("TestLanguage - Text",
                                  "Text",
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.Empty,
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT),
                new ColorableItem("TestLanguage - Keyword",
                                  "Keyword",
                                  COLORINDEX.CI_MAROON,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.FromArgb(192,32,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_BOLD),
                new ColorableItem("TestLanguage - Comment",
                                  "Comment",
                                  COLORINDEX.CI_DARKGREEN,
                                  COLORINDEX.CI_LIGHTGRAY,
                                  System.Drawing.Color.FromArgb(32,128,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT)
                // ...
                // Add as many colorable items as you want to support.
            };
        }
    }
}
```

## <a name="the-colorizer-class-and-the-scanner"></a>Classe colorante e scanner
 La classe di base <xref:Microsoft.VisualStudio.Package.LanguageService> dispone di un metodo <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> che instantiantes la classe <xref:Microsoft.VisualStudio.Package.Colorizer>. Lo scanner restituito dal metodo <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> viene passato al costruttore della classe <xref:Microsoft.VisualStudio.Package.Colorizer>.

 È necessario implementare il metodo <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> nella propria versione della classe <xref:Microsoft.VisualStudio.Package.LanguageService>. La classe <xref:Microsoft.VisualStudio.Package.Colorizer> usa lo scanner per ottenere tutte le informazioni sul colore del token.

 Lo scanner deve popolare una struttura di <xref:Microsoft.VisualStudio.Package.TokenInfo> per ogni token rilevato. Questa struttura contiene informazioni quali l'intervallo di occupare del token, l'indice dei colori da usare, il tipo di token e i trigger del token (vedere <xref:Microsoft.VisualStudio.Package.TokenTriggers>). Solo l'indice span e color sono necessari per la colorazione da parte della classe <xref:Microsoft.VisualStudio.Package.Colorizer>.

 L'indice dei colori archiviato nella struttura <xref:Microsoft.VisualStudio.Package.TokenInfo> è in genere un valore dell'enumerazione <xref:Microsoft.VisualStudio.Package.TokenColor>, che fornisce un numero di indici denominati corrispondenti a vari elementi del linguaggio, ad esempio parole chiave e operatori. Se l'elenco elementi colorabili personalizzati corrisponde agli elementi presentati nell'enumerazione <xref:Microsoft.VisualStudio.Package.TokenColor>, è possibile usare semplicemente l'enumerazione come colore per ogni token. Tuttavia, se si dispone di elementi colorabili aggiuntivi o non si desidera utilizzare i valori esistenti in tale ordine, è possibile disporre l'elenco elementi colorabili personalizzati in base alle proprie esigenze e restituire l'indice appropriato in tale elenco. Assicurarsi di eseguire il cast dell'indice a un <xref:Microsoft.VisualStudio.Package.TokenColor> durante l'archiviazione nella struttura <xref:Microsoft.VisualStudio.Package.TokenInfo>;  [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] Visualizza solo l'indice.

### <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato come lo scanner potrebbe identificare tre tipi di token: numeri, punteggiatura e identificatori (qualsiasi elemento che non sia un numero o una punteggiatura). Questo esempio è solo a scopo illustrativo e non rappresenta un'implementazione completa del parser e dello scanner. Si presuppone che esista una classe `Lexer` con un metodo `GetNextToken()` che restituisce una stringa.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    private Lexer lex;

    public class TestScanner : IScanner
    {
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                }
                else if (Char.IsNumber(firstChar))
                {
                    tokenInfo.Type = TokenType.Literal;
                    tokenInfo.Color = TokenColor.Number;
                }
                else
                {
                    tokenInfo.Type = TokenType.Identifier;
                    tokenInfo.Color = TokenColor.Identifier;
                }
            }
            return foundToken;
        }
```

## <a name="see-also"></a>Vedere anche
- [Funzionalità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)
- [Scanner e parser dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
- [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)