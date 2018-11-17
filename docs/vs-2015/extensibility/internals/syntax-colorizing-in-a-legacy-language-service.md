---
title: Colorazione della sintassi in un servizio di linguaggio Legacy | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20655534439fa187488087e1ae819a7ffca4c27a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730275"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Colorazione della sintassi in un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La colorazione della sintassi è una funzionalità che fa sì che diversi elementi di un linguaggio di programmazione da visualizzare in un file di origine in diversi colori e stili. Per supportare questa funzionalità, è necessario fornire un parser o lo scanner in grado di identificare i tipi di elementi lessicali o token nel file. Molti linguaggi di distinguono le parole chiave, delimitatori (ad esempio parentesi o parentesi graffe) e i commenti da colorare loro in modi diversi.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni, vedere [estensione dell'Editor e servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  È consigliabile che si inizia a usare il nuovo editor delle API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="implementation"></a>Implementazione  
 Per supportare la colorazione, il framework di pacchetto gestito (MPF) include il <xref:Microsoft.VisualStudio.Package.Colorizer> classe che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfaccia. Questa classe interagisce con un <xref:Microsoft.VisualStudio.Package.IScanner> per determinare il token e i colori. Per altre informazioni su scanner, vedere [Scanner e Parser servizio di linguaggio Legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). Il <xref:Microsoft.VisualStudio.Package.Colorizer> classe quindi contrassegna ogni carattere del token con le informazioni sul colore e restituisce le informazioni nell'editor contenente il file di origine.  
  
 Le informazioni sul colore restituiti all'editor è un indice in un elenco di elementi colorabili. Ogni elemento colorabile specifica un valore di colore e un set di attributi del tipo di carattere, ad esempio grassetto o barrato. L'editor fornisce un set di elementi colorabili predefiniti che è possibile usare il servizio di linguaggio. Tutto è necessario eseguire è specificare l'indice di colore appropriato per ogni tipo di token. Tuttavia, è possibile fornire un set di elementi colorabili personalizzati e gli indici che è fornire per i token e fare riferimento a un elenco personalizzato di elementi colorabili anziché l'elenco predefinito. È necessario impostare anche il `RequestStockColors` voce del Registro di sistema su 0 (o non si specifica il `RequestStockColors` voce affatto) per supportare i colori personalizzati. È possibile impostare questa voce del Registro di sistema con un parametro denominato per il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attributo definito dall'utente. Per altre informazioni sulla registrazione di un servizio di linguaggio e l'impostazione delle opzioni, vedere [la registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## <a name="custom-colorable-items"></a>Elementi colorabili personalizzati  
 Per fornire i propri elementi colorabili personalizzati, è necessario eseguire l'override di <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> e <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> metodo su di <xref:Microsoft.VisualStudio.Package.LanguageService> classe. Il primo metodo restituisce il numero di elementi colorabili personalizzati supportati dal servizio di linguaggio e il secondo Ottiene l'elemento colorabile personalizzato in base all'indice. Si crea l'elenco predefinito di elementi colorabili personalizzati. Nel costruttore del servizio di linguaggio, tutto è necessario eseguire è specificare ogni elemento colorabile con un nome. Visual Studio gestisce automaticamente il caso in cui l'utente seleziona un set diverso di elementi colorabili. Questo nome viene visualizzato un messaggio nel **tipi di carattere e colori** pagina delle proprietà nel **opzioni** la finestra di dialogo (disponibile da Visual Studio **strumenti** menu) e questo nome determina quali colore di che un utente ha eseguito l'override. Le scelte dell'utente sono archiviate in una cache nel Registro di sistema e a cui accede il nome del colore. Il **tipi di carattere e colori** pagina delle proprietà sono elencati tutti i nomi di colore in ordine alfabetico, in modo che è possibile raggruppare i colori personalizzati per ciascun nome preceduto dal colore con il nome del linguaggio; ad esempio, "**TestLanguage commento**"e"**TestLanguage - parola chiave**". Oppure è possibile raggruppare gli elementi colorabili dal tipo, "**commento (TestLanguage)**"e"**parola chiave (TestLanguage)**". Raggruppamento in base al nome della lingua è preferito.  
  
> [!CAUTION]
>  Si consiglia di includere il nome della lingua nel nome dell'elemento colorabile per evitare conflitti con nomi di elemento colorabile esistenti.  
  
> [!NOTE]
>  Se si modifica il nome di uno dei colori durante lo sviluppo, è necessario reimpostare la cache che Visual Studio ha creato la prima volta che i colori ha eseguito l'accesso. È possibile farlo eseguendo il **reimpostare l'Hive sperimentale** dal menu di programma Visual Studio SDK.  
  
 Si noti che il primo elemento nell'elenco di elementi colorabili non viene mai fatto riferimento. Visual Studio sono disponibili sempre i colori del testo predefinito e attributi per quell'elemento. Il modo più semplice di gestire questa situazione è fornire un elemento colorabile segnaposto come primo elemento.  
  
### <a name="high-color-colorable-items"></a>Elementi colorabili High Color  
 Gli elementi colorabili possono supportare anche valori di colore a 24 bit o elevata attraverso la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaccia. MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> supportate dalla classe di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaccia e i colori a 24 bit vengono specificati nel costruttore con i colori normali. Per ulteriori dettagli, vedere la classe <xref:Microsoft.VisualStudio.Package.ColorableItem>. L'esempio seguente viene illustrato come impostare i colori a 24 bit per le parole chiave e i commenti. I colori a 24 bit vengono usati quando colori a 24 bit sono supportato sul desktop dell'utente; in caso contrario, vengono usati i colori del testo normale.  
  
 Tenere presente che questi sono i colori predefiniti per il linguaggio. l'utente può modificare i colori come desiderano.  
  
### <a name="example"></a>Esempio  
 In questo esempio viene illustrato come dichiarare e popolare una matrice di elementi colorabili personalizzati usando il <xref:Microsoft.VisualStudio.Package.ColorableItem> classe. In questo esempio i colori (parola chiave) e il commento con colori a 24 bit.  
  
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
                new ColorableItem("TestLanguage – Text",  
                                  "Text",  
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.Empty,  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT),  
                new ColorableItem("TestLanguage – Keyword",  
                                  "Keyword",  
                                  COLORINDEX.CI_MAROON,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.FromArgb(192,32,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_BOLD),  
                new ColorableItem("TestLanguage – Comment",  
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
  
## <a name="the-colorizer-class-and-the-scanner"></a>La classe Colorizzatore e lo Scanner  
 La base <xref:Microsoft.VisualStudio.Package.LanguageService> classe ha un <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> metodo tale instantiantes il <xref:Microsoft.VisualStudio.Package.Colorizer> classe. Lo scanner restituito dal <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> viene passato per il <xref:Microsoft.VisualStudio.Package.Colorizer> costruttore della classe.  
  
 È necessario implementare il <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodo in una versione personalizzata del <xref:Microsoft.VisualStudio.Package.LanguageService> classe. Il <xref:Microsoft.VisualStudio.Package.Colorizer> classe Usa lo scanner per ottenere tutte le informazioni di token di colore.  
  
 Lo scanner deve popolare un <xref:Microsoft.VisualStudio.Package.TokenInfo> struttura per ogni token si trova. Questa struttura contiene informazioni quali occupa l'intervallo del token, l'indice di colore da usare, quali il tipo è il token, token e i trigger (vedere <xref:Microsoft.VisualStudio.Package.TokenTriggers>). Sono necessari solo l'indice di intervallo e il colore per la colorazione per il <xref:Microsoft.VisualStudio.Package.Colorizer> classe.  
  
 L'indice di colore archiviato nel <xref:Microsoft.VisualStudio.Package.TokenInfo> struttura in genere è un valore compreso il <xref:Microsoft.VisualStudio.Package.TokenColor> enumerazione, che fornisce un numero di indici denominati corrispondente a vari elementi del linguaggio, ad esempio le parole chiave e gli operatori. Se gli elementi colorabili personalizzati Elenca i risultati presentati gli elementi nel <xref:Microsoft.VisualStudio.Package.TokenColor> enumerazione, è possibile semplicemente usare l'enumerazione come colore per ogni token. Tuttavia, se si dispone di elementi colorabili aggiuntivi o si preferisce non usare i valori esistenti nell'ordine indicato, è possibile disporre l'elenco di elementi colorabili personalizzati per soddisfare le esigenze e restituire l'indice appropriato in tale elenco. È sufficiente Assicurarsi di eseguire il cast dell'indice a un <xref:Microsoft.VisualStudio.Package.TokenColor> quando si archiviano nel <xref:Microsoft.VisualStudio.Package.TokenInfo> struttura; [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] vede solo l'indice.  
  
### <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come lo scanner potrebbe identificare tre tipi di token: identificatori (tutto ciò che non è un numero o punteggiatura), segni di punteggiatura e numeri. Questo esempio è solo a scopo illustrativo e non rappresenta un'implementazione completa dello scanner e parser. Si presuppone che esista una `Lexer` classe con un `GetNextToken()` metodo che restituisce una stringa.  
  
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
 [Funzionalità del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)   
 [Scanner e Parser servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)

