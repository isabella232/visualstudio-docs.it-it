---
title: Colorazione della sintassi in un servizio di linguaggio Legacy Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02723a09254255b98291cb921ae5ec091d8b9859
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704700"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Colorazione della sintassi in un servizio di linguaggio legacy
Colorazione della sintassi è una funzionalità che determina la visualizzazione di diversi elementi di un linguaggio di programmazione in un file di origine in colori e stili diversi. Per supportare questa funzionalità, è necessario fornire un parser o uno scanner in grado di identificare i tipi di elementi lessicali o token nel file. Molti linguaggi distinguono parole chiave, delimitatori (ad esempio parentesi o parentesi graffe) e commenti colorandoli in modi diversi.

 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni, vedere [Estensione dell'editor e](../../extensibility/extending-the-editor-and-language-services.md)dei servizi di linguaggio .

> [!NOTE]
> Si consiglia di iniziare a utilizzare la nuova API dell'editor il prima possibile. Ciò migliorerà le prestazioni del servizio di linguaggio e consentirà di sfruttare le nuove funzionalità dell'editor.

## <a name="implementation"></a>Implementazione
 Per supportare la colorazione, il framework <xref:Microsoft.VisualStudio.Package.Colorizer> del pacchetto gestito <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> (MPF) include la classe , che implementa l'interfaccia. Questa classe interagisce <xref:Microsoft.VisualStudio.Package.IScanner> con un per determinare il token e colori. Per ulteriori informazioni sugli scanner, vedere Parser e scanner del servizio di [linguaggio Legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). La <xref:Microsoft.VisualStudio.Package.Colorizer> classe contrassegna quindi ogni carattere del token con le informazioni sul colore e restituisce tali informazioni all'editor che visualizza il file di origine.

 Le informazioni sul colore restituite all'editor sono un indice in un elenco di elementi colorabili. Ogni elemento colorabile specifica un valore di colore e un set di attributi del carattere, ad esempio grassetto o barrato. L'editor fornisce un set di elementi colorabili predefiniti che il servizio di linguaggio può utilizzare. Tutto quello che dovete fare è specificare l'indice di colore appropriato per ogni tipo di token. Tuttavia, è possibile fornire un set di elementi colorabili personalizzati e gli indici forniti per i token e fare riferimento al proprio elenco di elementi colorabili anziché all'elenco predefinito. È inoltre necessario `RequestStockColors` impostare la voce del `RequestStockColors` Registro di sistema su 0 (o non specificare affatto la voce) per supportare i colori personalizzati. È possibile impostare questa voce del <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Registro di sistema con un parametro denominato sull'attributo definito dall'utente. Per ulteriori informazioni sulla registrazione di un servizio di linguaggio e sull'impostazione delle relative opzioni, vedere Registrazione di un servizio di [linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md).

## <a name="custom-colorable-items"></a>Elementi colorabili personalizzati
 Per fornire elementi colorabili personalizzati, è <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> necessario eseguire <xref:Microsoft.VisualStudio.Package.LanguageService> l'override del metodo e sulla classe . Il primo metodo restituisce il numero di elementi colorabili personalizzati supportati dal servizio di linguaggio e il secondo ottiene l'elemento colorabile personalizzato in base all'indice. Creare l'elenco predefinito di elementi colorabili personalizzati. Nel costruttore del servizio di linguaggio, è sufficiente fornire un nome a ogni elemento colorabile. Visual Studio gestisce automaticamente il caso in cui l'utente seleziona un set diverso di elementi colorabili. Questo nome viene visualizzato nella pagina delle proprietà **Tipi di carattere e colori** della finestra di dialogo **Opzioni** (disponibile dal menu **Strumenti** di Visual Studio) e determina il colore sostituito da un utente. Le scelte dell'utente vengono memorizzate in una cache nel Registro di sistema e vi si accede tramite il nome del colore. La pagina delle proprietà **Tipi di carattere e colori** elenca tutti i nomi dei colori in ordine alfabetico, in modo da poter raggruppare i colori personalizzati facendo precedere ogni nome di colore dal nome della lingua. ad esempio, "**TestLanguage- Comment**" e "**TestLanguage- Parola chiave**". Oppure è possibile raggruppare gli elementi colorabili per tipo, "**Comment (TestLanguage)**" e "**Parola chiave (TestLanguage)**". È preferibile raggruppare in base al nome della lingua.

> [!CAUTION]
> Si consiglia di includere il nome della lingua nel nome dell'elemento colorabile per evitare conflitti con i nomi degli elementi colorabili esistenti.

> [!NOTE]
> Se si modifica il nome di uno dei colori durante lo sviluppo, è necessario reimpostare la cache creata da Visual Studio al primo accesso ai colori. A tale scopo, eseguire il comando **Reimposta Hive sperimentale** dal menu del programma Visual Studio SDK.

 Si noti che il primo elemento nell'elenco di elementi colorabili non viene mai fatto riferimento. Visual Studio fornisce sempre i colori e gli attributi di testo predefiniti per l'elemento. Il modo più semplice per gestire questa situazione consiste nel fornire un elemento colorabile segnaposto come primo elemento.

### <a name="high-color-colorable-items"></a>Elementi colorabili ad alto colore
 Gli elementi colorabili possono anche supportare valori <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> di colore a 24 bit o alti tramite l'interfaccia. La classe <xref:Microsoft.VisualStudio.Package.ColorableItem> MPF <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> supporta l'interfaccia e i colori a 24 bit vengono specificati nel costruttore insieme ai colori normali. Per ulteriori dettagli, vedere la classe <xref:Microsoft.VisualStudio.Package.ColorableItem>. L'esempio seguente mostra come impostare i colori a 24 bit per parole chiave e commenti. I colori a 24 bit vengono utilizzati quando il colore a 24 bit è supportato sul desktop dell'utente; in caso contrario, vengono utilizzati i normali colori del testo.

 Ricordate, questi sono i colori predefiniti per la vostra lingua; l'utente può modificare questi colori a quello che vuole.

### <a name="example"></a>Esempio
 In questo esempio viene illustrato un modo per dichiarare <xref:Microsoft.VisualStudio.Package.ColorableItem> e popolare una matrice di elementi colorabili personalizzati utilizzando la classe . In questo esempio vengono impostati i colori della parola chiave e del commento utilizzando colori a 24 bit.

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

## <a name="the-colorizer-class-and-the-scanner"></a>La classe Colorizer e lo Scanner
 La <xref:Microsoft.VisualStudio.Package.LanguageService> classe base <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> dispone di un <xref:Microsoft.VisualStudio.Package.Colorizer> metodo che crea un'istanza della classe. Lo scanner restituito dal <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodo viene passato <xref:Microsoft.VisualStudio.Package.Colorizer> al costruttore della classe.

 È necessario <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> implementare il metodo <xref:Microsoft.VisualStudio.Package.LanguageService> nella propria versione della classe. La <xref:Microsoft.VisualStudio.Package.Colorizer> classe utilizza lo scanner per ottenere tutte le informazioni sul colore dei token.

 Lo scanner deve <xref:Microsoft.VisualStudio.Package.TokenInfo> popolare una struttura per ogni token trovato. Questa struttura contiene informazioni quali l'intervallo che occupa il token, l'indice dei colori <xref:Microsoft.VisualStudio.Package.TokenTriggers>da utilizzare, il tipo di token e i trigger del token (vedere ). Solo l'intervallo e l'indice <xref:Microsoft.VisualStudio.Package.Colorizer> del colore sono necessari per la colorazione da parte della classe.

 L'indice di <xref:Microsoft.VisualStudio.Package.TokenInfo> colore archiviato nella <xref:Microsoft.VisualStudio.Package.TokenColor> struttura è in genere un valore dell'enumerazione , che fornisce un numero di indici denominati corrispondenti a vari elementi del linguaggio, ad esempio parole chiave e operatori. Se l'elenco di elementi colorabili <xref:Microsoft.VisualStudio.Package.TokenColor> personalizzati corrisponde agli elementi presentati nell'enumerazione, è possibile usare l'enumerazione come colore per ogni token. Tuttavia, se si dispone di elementi colorabili aggiuntivi o non si desidera utilizzare i valori esistenti in tale ordine, è possibile disporre l'elenco di elementi colorabili personalizzati in base alle proprie esigenze e restituire l'indice appropriato in tale elenco. Basta essere sicuri di eseguire <xref:Microsoft.VisualStudio.Package.TokenColor> il cast <xref:Microsoft.VisualStudio.Package.TokenInfo> dell'indice su un quando lo si memorizza nella struttura; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] vede solo l'indice.

### <a name="example"></a>Esempio
 L'esempio seguente mostra come lo scanner potrebbe identificare tre tipi di token: numeri, punteggiatura e identificatori (qualsiasi elemento che non sia un numero o punteggiatura). Questo esempio è solo a scopo illustrativo e non rappresenta un'implementazione completa del parser e dello scanner. Si presuppone che vi `Lexer` sia `GetNextToken()` una classe con un metodo che restituisce una stringa.

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
