---
title: La registrazione di un tipo di linguaggio legacy2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 07d70bb1d77dc3022b06c4036317e31692307f98
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188843"
---
# <a name="registering-a-legacy-language-service"></a>La registrazione di un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le sezioni seguenti forniscono gli elenchi di voci del Registro di sistema per la lingua diverse opzioni di servizio disponibili in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Nel seguente elenco di voci del Registro di sistema, *principale di Visual Studio Reg* è uguale a HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*x. y*, dove *x. y* è la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] numero di versione.  
  
## <a name="registry-entries-for-language-service-options"></a>Voci del Registro di sistema per le opzioni di servizio di linguaggio  
 Il *VS Reg radice*Services \Languages\Language\\*nome del linguaggio* chiave può contenere i valori seguenti.  
  
|Name|Type|Intervallo|DESCRIZIONE|  
|----------|----------|-----------|-----------------|  
|(Predefinito)|REG_SZ|*\<GUID>*|GUID del servizio di linguaggio.|  
|LangResID|REG_DWORD|0x0-0xffff|Stringa identificatore di risorsa (ResID) per il nome del testo localizzato del linguaggio.|  
|Pacchetto|REG_SZ|*\<GUID>*|GUID del pacchetto VSPackage.|  
|ShowCompletion|REG_DWORD|0-1|Specifica se il **completamento delle istruzioni** le opzioni presenti nella **opzioni** sono abilitate nella finestra di dialogo.|  
|ShowSmartIndent|REG_DWORD|0-1|Specifica se l'opzione per selezionare **intelligente** rientri nel **opzioni** nella finestra di dialogo è abilitata.|  
|RequestStockColors|REG_DWORD|0-1|Specifica se personalizzato o i colori predefiniti vengono utilizzati per colorare le parole chiave.|  
|ShowHotURLs|REG_DWORD|0-1|Specifica se l'utente può scegliere gli URL.|  
|Per impostazione predefinita Non Hot URL|REG_DWORD|0-1|Specifica l'impostazione iniziale per il **Consenti navigazione URL con clic singolo** opzione il **opzioni** nella finestra di dialogo.|  
|DefaultToInsertSpaces|REG_DWORD|0-1|Specifica se il servizio di linguaggio ha "inserire spazi" come l'opzione di scheda predefinita.|  
|ShowDropdownBarOption|REG_DWORD|0-1|Abilita o disabilita il **barra di spostamento** opzione il **opzioni** la finestra di dialogo che visualizza o nasconde il **barra di spostamento**.|  
|Solo finestra del codice singolo|REG_DWORD|0-1|Abilita o disabilita il **nuova finestra** scelte nel **finestra** menu per un servizio di linguaggio.|  
|EnableAdvancedMembersOption|REG_DWORD|0-1|Abilita o disabilita un' **le opzioni** impostazione di finestra di dialogo per **Nascondi membri avanzati**.|  
|Supporto CF_HTML|REG_DWORD|0-1|Specifica se l'editor consente di copiare e incollare dati HTML.|  
|EnableLineNumbersOption|REG_DWORD|0-1|Specifica se il **numeri di riga** le opzioni presenti nella **opzioni** nella finestra di dialogo è abilitata per un servizio di linguaggio.|  
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Specifica se i membri avanzati, ad esempio campi privati sono nascoste in elenchi di completamento.|  
|ShowBraceCompletion|REG_DWORD|0-1|Specifica se il **delimitare tra parentesi graffe completamento** opzione il **opzioni** nella finestra di dialogo è abilitata.|  
  
### <a name="example"></a>Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
        LangResID             = reg_dword:0x00000000  
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}  
        ShowCompletion        = reg_dword:0x00000001  
        ShowSmartIndent       = reg_dword:0x00000001  
        ShowDropdownBarOption = reg_dword:0x00000001  
```  
  
## <a name="registry-entries-for-debugger-languages-options"></a>Voci del Registro di sistema per le opzioni di linguaggi di Debugger  
 Il *VS Reg radice*Services \Languages\Language\\*nome del linguaggio*\Debugger lingue\\*GUID*\ chiave può includere quanto segue valori.  
  
|Name|Type|Intervallo|Descrizione|  
|----------|----------|-----------|-----------------|  
|(Predefinito)|REG_SZ|text|Il valore predefinito è utilizzabile per il nome del linguaggio del documento. Il nome di questa chiave è un GUID di un analizzatore di espressioni che ha una voce corrispondente in  *\<VS Reg radice >* \AD7Metrics\Expression dell'analizzatore di espressioni.|  
  
### <a name="example"></a>Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      C/C++\  
        Debugger Languages\  
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\  
            (Default) = reg_sz:C++  
```  
  
## <a name="registry-entries-for-editor-tools-options"></a>Voci del Registro di sistema per le opzioni degli strumenti Editor  
 È possibile aggiungere le chiavi del Registro di sistema nella chiave EditorToolsOptions per le pagine delle proprietà e i nodi di proprietà. Queste chiavi e i relativi valori identificano pagine delle proprietà nel **opzioni** nella finestra di dialogo (nelle **strumenti** menu) che vengono usate per configurare il servizio di linguaggio. Nell'esempio seguente *nome della pagina* è il nome di una pagina delle proprietà, e *nome del nodo* è il nome di un nodo dell'albero nel **opzioni** nella finestra di dialogo. La voce della pagina e la voce del nodo devono essere specificati separatamente.  
  
|Name|Type|Intervallo|DESCRIZIONE|  
|----------|----------|-----------|-----------------|  
|(Predefinito)|REG_SZ|resID|Il nome visualizzato localizzato di questa pagina di opzioni. Il nome può essere testo letterale o un &`nnn`, dove `nnn` è un ID di risorsa stringa nella DLL del pacchetto VSPackage specificato satellite.|  
|Pacchetto|REG_SZ|*GUID*|Il GUID del pacchetto VSPackage che implementa questa pagina di opzioni.|  
|Pagina|REG_SZ|*GUID*|Il GUID della pagina delle proprietà per richiedere da VSPackage mediante la chiamata di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> (metodo). Se questa voce del Registro di sistema non è presente, la chiave del Registro di sistema descrive un nodo, non una pagina.|  
  
### <a name="example"></a>Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      CSharp\  
        EditorToolsOptions\  
          Formatting\  
            (Default) = reg_sz:#242  
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
            General\  
              (Default) = reg_sz:#255  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}  
            Indentation\  
              (Default) = reg_sz:#250  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}  
            Newlines\  
              (Default) = reg_sz:#253  
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}  
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}  
```  
  
## <a name="registry-entries-for-file-name-extension-options"></a>Voci del Registro di sistema per le opzioni dell'estensione nome File  
 La voce per l'estensione del file deve includere il punto iniziale, ad esempio ".myext".  
  
|Name|Type|Intervallo|Descrizione|  
|----------|----------|-----------|-----------------|  
|(Predefinito)|REG_SZ|*GUID*|GUID del servizio per il servizio di linguaggio predefinito per questo tipo di estensione nome file.|  
  
### <a name="example"></a>Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    File Extensions\  
      .cpp\  
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}  
```  
  
## <a name="registry-entries-for-editor-options"></a>Voci del Registro di sistema per le opzioni dell'Editor  
 Il *VS Reg radice*\Editors chiave può contenere i valori seguenti:  
  
|NOME|Type|Intervallo|Descrizione|  
|----------|----------|-----------|-----------------|  
|(Predefinito)|REG_SZ|""|Inutilizzate; è possibile inserire qui il nome per la documentazione.|  
|DefaultToolboxTab|REG_SZ|""|Nome della scheda della casella degli strumenti per impostare come predefinito quando l'editor è attivo.|  
|DisplayName|REG_SZ|resID|Nome da visualizzare nella **aperta con** nella finestra di dialogo. Il nome è un nome o l'ID di risorsa stringa in formato standard.|  
|ExcludeDefTextEditor|REG_DWORD|0-1|Utilizzato per il **aperta con** comando di menu. Se non vuoi elenco l'editor di testo predefinito nell'elenco degli editor disponibili per un tipo di file specifico, impostare questo valore su 1.|  
|LinkedEditorGUID|REG_SZ|*\<GUID>*|Usato per qualsiasi servizio di linguaggio che è possibile aprire un file con il supporto tabella codici. Ad esempio, quando si apre un file con estensione txt con il **Apri con** comando, sono disponibili opzioni per l'utilizzo di editor del codice sorgente con e senza codifica.<br /><br /> Il GUID specificato il nome della sottochiave è per la factory dell'editor tabella codici; il GUID collegato specificato in questa voce del Registro di sistema specifiche sia per la factory dell'editor regolari. Lo scopo di questa voce è che se l'IDE non si apre un file usando l'editor predefinito, l'IDE proverà a usare l'editor successivo nell'elenco. Questo editor successivo non deve essere la factory dell'editor tabella codici perché la factory dell'editor è fondamentalmente quello utilizzato per la factory dell'editor che non è riuscita.|  
|Pacchetto|REG_SZ|*\<GUID>*|GUID VSPackage ResID del nome visualizzato.|  
  
### <a name="example"></a>Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      (Default)            = reg_sz:Html Editor with Encoding  
      DefaultToolboxTab    = reg_sz:HTML  
      DisplayName          = reg_sz:#20101  
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}  
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}  
```  
  
## <a name="registry-entries-for-logical-view-options"></a>Voci del Registro di sistema per le opzioni di visualizzazione logica  
 Il *principale di Visual Studio Reg*\Editors\\*GUI dell'Editor >* \LogicalViews chiave può contenere i valori seguenti.  
  
|Name|Type|Intervallo|Descrizione|  
|----------|----------|-----------|-----------------|  
|(Predefinito)|REG_SZ||Non usato.|  
|*\<GUID>*|REG_SZ|""|Chiave per le visualizzazioni logiche supportate. È possibile avere tutti gli elementi in base alle esigenze. Il nome della voce del Registro di sistema è ciò che è importante, non il valore, che è sempre una stringa vuota.|  
  
### <a name="example"></a>Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      LogicalViews\  
       (Default) = reg_sz:  
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:  
```  
  
## <a name="registry-entries-for-editor-extension-options"></a>Voci del Registro di sistema per le opzioni dell'estensione di Editor  
 Il *principale di Visual Studio Reg*\Editors\\*GUID dell'Editor*\Extensions chiave può contenere i valori seguenti. L'estensione del nome file non include il punto iniziale.  
  
|NOME|Type|Intervallo|DESCRIZIONE|  
|----------|----------|-----------|-----------------|  
|(Predefinito)|REG_SZ||Non usato.|  
|*\<ext>*|REG_DWORD|0-0xffffffff|Priorità relativa delle estensioni. Se due o più lingue condividono la stessa estensione, viene scelta la lingua con priorità più alta.|  
  
 Inoltre, selezione predefinita dell'utente corrente per un editor viene archiviata in HKEY_Current_User\Software\Microsoft\VisualStudio\\*x. y*\Default editor\\*ext*. Il GUID del servizio di linguaggio selezionato sia nella voce di personalizzati. Questo ha la precedenza per l'utente corrente.  
  
### <a name="example"></a>Esempio  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\  
  \Editors\  
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\  
      Extensions\  
       (Default) = reg_sz:  
       *         = reg_dword:0x00000018  
       html      = reg_dword:0x00000027  
       shtm      = reg_dword:0x00000027  
       shtml     = reg_dword:0x00000027  
```  
  
## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Voci del Registro di sistema per Opzioni Servizio linguaggio Framework di pacchetto gestito  
 Le voci del Registro di sistema seguenti sono specifiche per le classi del servizio gestito del pacchetto framework (MPF) della lingua. Queste voci del Registro di sistema indicano il supporto del servizio di linguaggio per varie funzionalità di IntelliSense e altre funzionalità di modifica avanzate.  
  
 Queste voci del Registro di sistema sono accessibili tramite il <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
|NOME|Type|Intervallo|DESCRIZIONE|  
|----------|----------|-----------|-----------------|  
|CodeSense|REG_DWORD|0-1|Supporto per le operazioni IntelliSense.|  
|MatchBraces|REG_DWORD|0-1|Supporto per la corrispondenza di coppie di linguaggi, ad esempio le parentesi graffe, parentesi e parentesi quadre.|  
|Informazioni rapide|REG_DWORD|0-1|Supporto per l'operazione di informazioni rapide di IntelliSense.|  
|ShowMatchingBrace|REG_DWORD|0-1|Supporto per la visualizzazione la coppia di linguaggi corrispondente nella barra di stato.|  
|MatchBracesAtCaret|REG_DWORD|0-1|Supporto per la visualizzazione delle coppie di linguaggi corrispondenti, in genere mediante l'evidenziazione i due elementi.|  
|MaxErrorMessages|REG_DWORD|0-n|Il numero massimo di errori che possono essere visualizzati nei **elenco errori** finestra.|  
|CodeSenseDelay|REG_DWORD|0-n|Il numero di millisecondi di ritardo prima di avviare qualsiasi analisi per un'operazione di IntelliSense in background.|  
|EnableAsyncCompletion|REG_DWORD|0-1|Supporto per l'analisi in background.|  
|EnableCommenting|REG_DWORD|0-1|Il supporto per blocchi di testo selezionati come commento e implica anche il supporto per la rimozione dei commenti sul testo selezionato.|  
|EnableFormatSelection|REG_DWORD|0-1|Supporto per la formattazione del testo, ad esempio rientro automatico o a modificare la posizione delle parentesi graffe.|  
|AutoOutlining|REG_DWORD|0-1|Supporto per la struttura (aree che possono essere compressi).|  
|MaxRegions|REG_DWORD|0-n|Il numero massimo di aree nascoste per ogni file.|  
  
```  
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\  
  Languages\  
    Language Services\  
      XML\  
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}  
        MatchBraces           = reg_dword:0x00000001  
        QuickInfo             = reg_dword:0x00000001  
        ShowMatchingBrace     = reg_dword:0x00000001  
        MatchBracesAtCaret    = reg_dword:0x00000000  
        MaxErrorMessages      = reg_dword:0x00000064  
        CodeSenseDelay        = reg_dword:0x000001f4  
        MaxRegions            = reg_dword:0x0000000a  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)
