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
ms.openlocfilehash: 1f6e9a5b1ee616157e0a79c41335640da0a3434d1115848b754c3c2a3e4c7e8f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414168"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Colorazione della sintassi in un servizio di linguaggio legacy
La colorazione della sintassi è una funzionalità che fa sì che diversi elementi di un linguaggio di programmazione siano visualizzati in un file di origine con colori e stili diversi. Per supportare questa funzionalità, è necessario fornire un parser o uno scanner in grado di identificare i tipi di elementi lessicali o token nel file. Molti linguaggi distinguono parole chiave, delimitatori (ad esempio parentesi o parentesi graffe) e commenti colorandoli in modi diversi.

 I servizi di linguaggio legacy vengono implementati come parte di un PACCHETTO VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni, vedere Estensione [dell'editor e dei servizi di linguaggio.](../../extensibility/extending-the-editor-and-language-services.md)

> [!NOTE]
> È consigliabile iniziare a usare la nuova API dell'editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare le nuove funzionalità dell'editor.

## <a name="implementation"></a>Implementazione
 Per supportare la colorazione, il framework del pacchetto gestito (MPF) include la <xref:Microsoft.VisualStudio.Package.Colorizer> classe , che implementa l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> . Questa classe interagisce con un oggetto <xref:Microsoft.VisualStudio.Package.IScanner> per determinare il token e i colori. Per altre informazioni sugli scanner, vedere Parser e scanner del [servizio di linguaggio legacy.](../../extensibility/internals/legacy-language-service-parser-and-scanner.md) La classe contrassegna quindi ogni carattere del token con le informazioni sul colore e <xref:Microsoft.VisualStudio.Package.Colorizer> restituisce le informazioni all'editor che visualizza il file di origine.

 Le informazioni sul colore restituite all'editor sono un indice in un elenco di elementi colorabili. Ogni elemento colorabile specifica un valore di colore e un set di attributi del carattere, ad esempio grassetto o barrato. L'editor fornisce un set di elementi colorabili predefiniti che possono essere utilizzati dal servizio di linguaggio. È necessario specificare l'indice colori appropriato per ogni tipo di token. È tuttavia possibile fornire un set di elementi colorabili personalizzati e gli indici forniti per i token e fare riferimento al proprio elenco di elementi colorabili anziché all'elenco predefinito. È inoltre necessario impostare la voce del Registro di sistema su 0 (o non specificare affatto la voce) per `RequestStockColors` `RequestStockColors` supportare i colori personalizzati. È possibile impostare questa voce del Registro di sistema con un parametro denominato <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> sull'attributo definito dall'utente. Per altre informazioni sulla registrazione di un servizio di linguaggio e sull'impostazione delle relative opzioni, vedere [Registrazione di un servizio di linguaggio legacy.](../../extensibility/internals/registering-a-legacy-language-service1.md)

## <a name="custom-colorable-items"></a>Elementi colorabili personalizzati
 Per fornire elementi colorabili personalizzati, è necessario eseguire l'override <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> del metodo e nella classe <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> . Il primo metodo restituisce il numero di elementi colorabili personalizzati supportati dal servizio di linguaggio e il secondo ottiene l'elemento colorabile personalizzato in base all'indice. Si crea l'elenco predefinito di elementi colorabili personalizzati. Nel costruttore del servizio di linguaggio è necessario specificare un nome per ogni elemento colorabile. Visual Studio gestisce automaticamente il caso in cui l'utente seleziona un set diverso di elementi colorabili. Questo nome viene visualizzato  nella pagina delle  proprietà Tipi di carattere e colori della finestra di dialogo Opzioni (disponibile nel **menu** Strumenti di Visual Studio) e questo nome determina il colore di cui un utente ha eseguito l'override. Le scelte dell'utente vengono archiviate in una cache nel Registro di sistema e vi si accede con il nome del colore. La **pagina delle proprietà Tipi** di carattere e colori elenca tutti i nomi dei colori in ordine alfabetico, pertanto è possibile raggruppare i colori personalizzati facendo precedere ogni nome di colore con il nome della lingua; ad esempio "**TestLanguage- Comment**" e "**TestLanguage- Keyword**". Oppure è possibile raggruppare gli elementi colorabili per tipo, "**Comment (TestLanguage)**" e "**Keyword (TestLanguage)**". È preferibile raggruppare in base al nome della lingua.

> [!CAUTION]
> È consigliabile includere il nome della lingua nel nome dell'elemento colorabile per evitare conflitti con i nomi di elementi colorabili esistenti.

> [!NOTE]
> Se si modifica il nome di uno dei colori durante lo sviluppo, è necessario reimpostare la cache creata Visual Studio la prima volta che si accede ai colori. A tale scopo, eseguire il comando Reset the Experimental Hive (Reimposta **Hive sperimentale)** dal menu Visual Studio programma SDK.

 Si noti che non viene mai fatto riferimento al primo elemento nell'elenco di elementi colorabili. Visual Studio fornisce sempre i colori di testo e gli attributi predefiniti per l'elemento. Il modo più semplice per gestire questo problema è fornire un elemento colorabile segnaposto come primo elemento.

### <a name="high-color-colorable-items"></a>Elementi colorabili a colori elevati
 Gli elementi colorabili possono supportare anche valori di colore a 24 bit o alti tramite <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> l'interfaccia . La classe MPF supporta l'interfaccia e i colori a 24 bit vengono specificati nel costruttore <xref:Microsoft.VisualStudio.Package.ColorableItem> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> insieme ai colori normali. Per ulteriori dettagli, vedere la classe <xref:Microsoft.VisualStudio.Package.ColorableItem>. L'esempio seguente illustra come impostare i colori a 24 bit per parole chiave e commenti. I colori a 24 bit vengono usati quando il colore a 24 bit è supportato sul desktop dell'utente; In caso contrario, vengono usati i colori del testo normali.

 Tenere presente che questi sono i colori predefiniti per la lingua. l'utente può modificare questi colori in base alle impostazioni desiderate.

### <a name="example"></a>Esempio
 Questo esempio illustra un modo per dichiarare e popolare una matrice di elementi colorabili personalizzati usando la <xref:Microsoft.VisualStudio.Package.ColorableItem> classe . In questo esempio vengono impostate le parole chiave e i colori dei commenti usando colori a 24 bit.

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

## <a name="the-colorizer-class-and-the-scanner"></a>La classe Colorizer e lo scanner
 La classe di base <xref:Microsoft.VisualStudio.Package.LanguageService> ha un metodo che crea <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> un'istanza della <xref:Microsoft.VisualStudio.Package.Colorizer> classe . Lo scanner restituito dal <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodo viene passato al costruttore della classe <xref:Microsoft.VisualStudio.Package.Colorizer> .

 È necessario <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> implementare il metodo nella propria versione della <xref:Microsoft.VisualStudio.Package.LanguageService> classe . La <xref:Microsoft.VisualStudio.Package.Colorizer> classe usa lo scanner per ottenere tutte le informazioni sul colore del token.

 Lo scanner deve popolare una struttura <xref:Microsoft.VisualStudio.Package.TokenInfo> per ogni token trovato. Questa struttura contiene informazioni come l'intervallo che occupa il token, l'indice colori da usare, il tipo di token e i trigger di token (vedere <xref:Microsoft.VisualStudio.Package.TokenTriggers> ). Solo l'intervallo e l'indice dei colori sono necessari per la colorazione da parte della <xref:Microsoft.VisualStudio.Package.Colorizer> classe .

 L'indice dei colori archiviato nella struttura è in genere un valore dell'enumerazione , che fornisce una serie di indici denominati corrispondenti a vari elementi del linguaggio, ad esempio parole <xref:Microsoft.VisualStudio.Package.TokenInfo> <xref:Microsoft.VisualStudio.Package.TokenColor> chiave e operatori. Se l'elenco personalizzato di elementi colorabili corrisponde agli elementi presentati nell'enumerazione , è possibile usare l'enumerazione come <xref:Microsoft.VisualStudio.Package.TokenColor> colore per ogni token. Tuttavia, se si dispone di elementi colorabili aggiuntivi o non si vogliono usare i valori esistenti in tale ordine, è possibile disporre l'elenco di elementi colorabili personalizzati in base alle proprie esigenze e restituire l'indice appropriato in tale elenco. È sufficiente assicurarsi di eseguire il cast dell'indice in un oggetto quando lo si archivia nella struttura . Visualizza <xref:Microsoft.VisualStudio.Package.TokenColor> <xref:Microsoft.VisualStudio.Package.TokenInfo> solo [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] l'indice.

### <a name="example"></a>Esempio
 L'esempio seguente mostra in che modo lo scanner può identificare tre tipi di token: numeri, punteggiatura e identificatori (qualsiasi elemento che non sia un numero o una punteggiatura). Questo esempio è solo a scopo illustrativo e non rappresenta un parser completo e un'implementazione dello scanner. Si presuppone che sia presente una `Lexer` classe con un metodo che restituisce una `GetNextToken()` stringa.

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
