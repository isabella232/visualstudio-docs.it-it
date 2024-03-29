---
title: Colorazione della sintassi in un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni su come supportare la colorazione della sintassi in un servizio di linguaggio legacy fornendo un parser o uno scanner in grado di identificare i tipi di elementi lessicali o token.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 906f144c6414d5af9483b046f49e3f911b30d0c4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626039"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Colorazione della sintassi in un servizio di linguaggio legacy
La colorazione della sintassi è una funzionalità che determina la visualizzazione di diversi elementi di un linguaggio di programmazione in un file di origine con colori e stili diversi. Per supportare questa funzionalità, è necessario fornire un parser o uno scanner in grado di identificare i tipi di elementi lessicali o token nel file. Molti linguaggi distinguono parole chiave, delimitatori (ad esempio parentesi o parentesi graffe) e commenti colorandoli in modi diversi.

 I servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni, vedere [Estensione dell'editor e di Servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> È consigliabile iniziare a usare la nuova API dell'editor appena possibile. In questo modo si miglioreranno le prestazioni del servizio di linguaggio e si potranno sfruttare le nuove funzionalità dell'editor.

## <a name="implementation"></a>Implementazione
 Per supportare la colorazione, il framework del pacchetto gestito (MPF) include la <xref:Microsoft.VisualStudio.Package.Colorizer> classe , che implementa l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> . Questa classe interagisce con un <xref:Microsoft.VisualStudio.Package.IScanner> oggetto per determinare il token e i colori. Per altre informazioni sugli scanner, vedere Parser e scanner del [servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). La classe contrassegna quindi ogni carattere del token con le informazioni sul colore e le restituisce <xref:Microsoft.VisualStudio.Package.Colorizer> all'editor che visualizza il file di origine.

 Le informazioni sul colore restituite all'editor sono un indice in un elenco di elementi colorabili. Ogni elemento colorabile specifica un valore di colore e un set di attributi del tipo di carattere, ad esempio grassetto o barrato. L'editor fornisce un set di elementi colorabili predefiniti che il servizio di linguaggio può usare. È necessario solo specificare l'indice colori appropriato per ogni tipo di token. È tuttavia possibile fornire un set di elementi colorabili personalizzati e gli indici forniti per i token e fare riferimento al proprio elenco di elementi colorabili anziché all'elenco predefinito. È anche necessario impostare la voce del Registro di sistema su 0 (o non specificare affatto la voce) per `RequestStockColors` `RequestStockColors` supportare i colori personalizzati. È possibile impostare questa voce del Registro di sistema con un parametro denominato <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> sull'attributo definito dall'utente. Per altre informazioni sulla registrazione di un servizio di linguaggio e sull'impostazione delle relative opzioni, vedere [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md).

## <a name="custom-colorable-items"></a>Elementi colorabili personalizzati
 Per fornire elementi colorabili personalizzati, è necessario eseguire l'override <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> del metodo e sulla classe <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> . Il primo metodo restituisce il numero di elementi colorabili personalizzati supportati dal servizio di linguaggio e il secondo ottiene l'elemento colorabile personalizzato in base all'indice. Si crea l'elenco predefinito di elementi colorabili personalizzati. Nel costruttore del servizio di linguaggio è necessario specificare un nome per ogni elemento colorabile. Visual Studio gestisce automaticamente il caso in cui l'utente seleziona un set diverso di elementi colorabili. Questo nome viene visualizzato  nella pagina delle  proprietà Tipi di carattere e colori della finestra di dialogo Opzioni (disponibile nel **menu** Strumenti Visual Studio) e questo nome determina il colore di cui un utente ha eseguito l'override. Le scelte dell'utente vengono archiviate in una cache nel Registro di sistema e a cui accede il nome del colore. La **pagina delle proprietà Tipi** di carattere e colori elenca tutti i nomi dei colori in ordine alfabetico, quindi è possibile raggruppare i colori personalizzati facendo precedere ogni nome di colore con il nome della lingua. ad esempio "**TestLanguage- Comment**" e "**TestLanguage- Parola chiave**". In caso contrario, è possibile raggruppare gli elementi colorabili in base al tipo "**Comment (TestLanguage)**" e "**Keyword (TestLanguage)**". È preferibile il raggruppamento in base al nome della lingua.

> [!CAUTION]
> È consigliabile includere il nome della lingua nel nome dell'elemento colorabile per evitare conflitti con i nomi di elementi colorabili esistenti.

> [!NOTE]
> Se si modifica il nome di uno dei colori durante lo sviluppo, è necessario reimpostare la cache Visual Studio la prima volta che si accede ai colori. A tale scopo, eseguire il comando Reset the Experimental Hive (Reimposta **hive sperimentale)** dal menu Visual Studio programma SDK.

 Si noti che non viene mai fatto riferimento al primo elemento nell'elenco di elementi colorabili. Visual Studio fornisce sempre i colori e gli attributi del testo predefiniti per l'elemento. Il modo più semplice per gestire questo problema è fornire un elemento colorabile segnaposto come primo elemento.

### <a name="high-color-colorable-items"></a>Elementi colorabili con colori elevati
 Gli elementi colorabili possono supportare anche valori di colore a 24 bit o alti tramite <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> l'interfaccia . La classe MPF supporta l'interfaccia e i colori a 24 bit vengono specificati nel costruttore <xref:Microsoft.VisualStudio.Package.ColorableItem> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> insieme ai colori normali. Per ulteriori dettagli, vedere la classe <xref:Microsoft.VisualStudio.Package.ColorableItem>. L'esempio seguente illustra come impostare i colori a 24 bit per parole chiave e commenti. I colori a 24 bit vengono usati quando il colore a 24 bit è supportato sul desktop dell'utente; In caso contrario, vengono usati i normali colori del testo.

 Tenere presente che si tratta dei colori predefiniti per la lingua. l'utente può modificare questi colori in base alle impostazioni desiderate.

### <a name="example"></a>Esempio
 Questo esempio illustra un modo per dichiarare e popolare una matrice di elementi colorabili personalizzati usando la <xref:Microsoft.VisualStudio.Package.ColorableItem> classe . In questo esempio vengono impostate la parola chiave e i colori dei commenti usando colori a 24 bit.

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

## <a name="the-colorizer-class-and-the-scanner"></a>Classe Colorizer e scanner
 La classe base <xref:Microsoft.VisualStudio.Package.LanguageService> ha un metodo che crea <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> un'istanza della <xref:Microsoft.VisualStudio.Package.Colorizer> classe . Lo scanner restituito dal <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodo viene passato al costruttore della <xref:Microsoft.VisualStudio.Package.Colorizer> classe.

 È necessario <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> implementare il metodo nella propria versione della <xref:Microsoft.VisualStudio.Package.LanguageService> classe . La <xref:Microsoft.VisualStudio.Package.Colorizer> classe usa lo scanner per ottenere tutte le informazioni sul colore del token.

 Lo scanner deve popolare una <xref:Microsoft.VisualStudio.Package.TokenInfo> struttura per ogni token trovato. Questa struttura contiene informazioni quali l'intervallo che occupa il token, l'indice colori da usare, il tipo di token e i trigger di token (vedere <xref:Microsoft.VisualStudio.Package.TokenTriggers> ). Solo l'intervallo e l'indice dei colori sono necessari per la colorazione da parte della <xref:Microsoft.VisualStudio.Package.Colorizer> classe .

 L'indice dei colori archiviato nella struttura è in genere un valore dell'enumerazione , che fornisce una serie di indici denominati corrispondenti a vari elementi del linguaggio, ad esempio parole <xref:Microsoft.VisualStudio.Package.TokenInfo> <xref:Microsoft.VisualStudio.Package.TokenColor> chiave e operatori. Se l'elenco di elementi colorabili personalizzati corrisponde agli elementi presentati nell'enumerazione , è possibile usare l'enumerazione come <xref:Microsoft.VisualStudio.Package.TokenColor> colore per ogni token. Tuttavia, se si dispone di elementi colorabili aggiuntivi o non si vogliono usare i valori esistenti in tale ordine, è possibile disporre l'elenco di elementi colorabili personalizzati in base alle proprie esigenze e restituire l'indice appropriato in tale elenco. Assicurarsi di eseguire il cast dell'indice su un oggetto quando lo si archivia nella struttura . Visualizza <xref:Microsoft.VisualStudio.Package.TokenColor> <xref:Microsoft.VisualStudio.Package.TokenInfo> solo [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] l'indice.

### <a name="example"></a>Esempio
 L'esempio seguente illustra come lo scanner può identificare tre tipi di token: numeri, punteggiatura e identificatori (qualsiasi valore che non sia un numero o una punteggiatura). Questo esempio è solo a scopo illustrativo e non rappresenta un'implementazione completa del parser e dello scanner. Presuppone che sia presente una `Lexer` classe con un metodo che restituisce una `GetNextToken()` stringa.

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

## <a name="see-also"></a>Vedi anche
- [Funzionalità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)
- [Scanner e parser dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
- [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)
