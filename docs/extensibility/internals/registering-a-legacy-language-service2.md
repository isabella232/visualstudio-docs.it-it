---
title: Registrazione di un servizio di linguaggio Legacy2 Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d9d13f301f6c04c0f7b14cc8c685f08b072ef84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705892"
---
# <a name="registering-a-legacy-language-service"></a>Registrazione di un servizio di linguaggio legacy
Nelle sezioni seguenti vengono forniti elenchi di voci del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Registro di sistema per le varie opzioni del servizio di linguaggio disponibili in .

 Nell'elenco di voci del Registro di sistema riportato di seguito, *VS Reg Root* è uguale a HKEY_LOCAL_MACHINE , SOFTWARE ,\\*X.Y*dove *X.Y* è il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] numero di versione.

## <a name="registry-entries-for-language-service-options"></a>Voci del Registro di sistema per le opzioni del servizio di linguaggioRegistry Entries for Language Service Options
 La chiave *VS Reg*Root\\, Languages , Language*Services Language Name* può contenere i valori seguenti.

|Nome|Type|Range|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ|*\<>GUID*|GUID del servizio di linguaggio.|
|LangResID (informazioni in lingua con gola)|REG_DWORD|0x0-0xffff|Identificatore di risorsa stringa (ResID) per il nome di testo localizzato della lingua.|
|Pacchetto|REG_SZ|*\<>GUID*|GUID del pacchetto VSPackage.|
|ShowCompletion (Dimostrazione di completamento|REG_DWORD|0-1|Specifica se le opzioni **di completamento dell'istruzione** nella finestra di dialogo **Opzioni** sono abilitate.|
|MostraIndent Smart|REG_DWORD|0-1|Specifica se l'opzione per selezionare Rientro **intelligente** nella finestra di dialogo **Opzioni** è attivata.|
|RichiestaDicolore|REG_DWORD|0-1|Specifica se i colori personalizzati o predefiniti vengono utilizzati per colorare le parole chiave.|
|ShowHotURLs|REG_DWORD|0-1|Specifica se l'utente può fare clic su URL.|
|Il valore predefinito è Non Hot URL|REG_DWORD|0-1|Specifica l'impostazione iniziale per l'opzione **di spostamento URL** con clic singolo nella finestra di dialogo **Opzioni.**|
|DefaultToInsertSpaces (Spazi predefiniti)|REG_DWORD|0-1|Specifica se il servizio di linguaggio ha "inserire spazi" come opzione di tabulazione predefinita.|
|ShowDropdownBarOption|REG_DWORD|0-1|Attiva o disattiva l'opzione **Barra di spostamento** nella finestra di dialogo **Opzioni** che mostra o nasconde la barra **di spostamento.**|
|Solo finestra codice singolo|REG_DWORD|0-1|Abilita o disabilita l'opzione **Nuova finestra** nel menu **Finestra** per un servizio di linguaggio.|
|EnableAdvancedMembersOption (Opzione AbiliAdvancedMembersOption)|REG_DWORD|0-1|Attiva o disattiva l'impostazione di una finestra di dialogo **Opzioni** per **Nascondi membri avanzati.**|
|CF_HTML di supporto|REG_DWORD|0-1|Specifica se l'editor abilita la copia e l'incollamento di dati HTML.|
|EnableLineNumbersOption|REG_DWORD|0-1|Specifica se le opzioni **Numeri di riga** nella finestra di dialogo **Opzioni** sono abilitate per un servizio di linguaggio.|
|NascondiAdvancedMembersByDefault|REG_DWORD|0-1|Specifica se i membri avanzati, ad esempio i campi privati, sono nascosti negli elenchi di completamento.|
|ShowBraceCompletion (Completamento di ShowBrace)ShowBrac|REG_DWORD|0-1|Specifica se l'opzione **Completamento controvento** nella finestra di dialogo **Opzioni** è attivata.|

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

## <a name="registry-entries-for-debugger-languages-options"></a>Voci del Registro di sistema per le opzioni dei linguaggi del debuggerRegistry Entries for Debugger Languages Options
 La chiave *VS Reg Root,* Languages, Language Services\\*Language Name*e Debugger Languages\\*GUID,* può includere i valori seguenti.

|Nome|Type|Range|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ|text|Il valore predefinito può essere utilizzato per documentare il nome della lingua. Il nome di questa chiave è un GUID di un * \< *analizzatore di espressioni che dispone di una voce corrispondente in VS Reg Root>, AD7Metrics , Expression Evaluator.|

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

## <a name="registry-entries-for-editor-tools-options"></a>Voci del Registro di sistema per le opzioni degli strumenti dell'editorRegistry Entries for Editor Tools Options
 È possibile aggiungere chiavi del Registro di sistema nella chiave EditorToolsOptions per le pagine delle proprietà e i nodi delle proprietà. Queste chiavi e i relativi valori identificano le pagine delle proprietà nella finestra di dialogo **Opzioni** (nel menu **Strumenti)** utilizzate per configurare il servizio di linguaggio. Nell'esempio seguente, *Nome pagina* è il nome di una pagina delle proprietà e *Nome nodo* è il nome di un nodo nella struttura nella finestra di dialogo **Opzioni.** La voce di pagina e la voce del nodo devono essere specificate separatamente.

|Nome|Type|Range|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ|Resid|Nome visualizzato localizzato di questa pagina di opzione. Il nome può essere testo`nnn`letterale, o , dove `nnn` è un ID di risorsa di stringa nella DLL satellite del pacchetto VSPackage specificato.|
|Pacchetto|REG_SZ|*Guid*|GUID del pacchetto VSPackage che implementa questa pagina di opzioni.|
|Pagina|REG_SZ|*Guid*|GUID della pagina delle proprietà da richiedere dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> pacchetto VSPackage chiamando il metodo . Se questa voce del Registro di sistema non è presente, la chiave del Registro di sistema descrive un nodo, non una pagina.|

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

## <a name="registry-entries-for-file-name-extension-options"></a>Voci del Registro di sistema per le opzioni di estensione dei nomi di fileRegistry Entries for File Name Extension Options
 La voce per l'estensione del file deve includere il periodo iniziale, ad esempio ".myext".

|Nome|Type|Range|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ|*Guid*|GUID del servizio per il servizio di linguaggio predefinito per questo tipo di estensione di file.|

### <a name="example"></a>Esempio

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>Voci del Registro di sistema per le opzioni dell'editorRegistry Entries for Editor Options
 La chiave *VS Reg Root*-Editors può contenere i seguenti valori:

|Nome|Type|Range|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ|""|Inutilizzato; si può mettere il proprio nome qui per la documentazione.|
|DefaultToolboxTab|REG_SZ|""|Nome della scheda della casella degli strumenti per impostare come predefinito quando l'editor è attivo.|
|DisplayName|REG_SZ|Resid|Nome da visualizzare nella finestra di dialogo **Apri con.** Il nome è l'ID di risorsa stringa o un nome in formato standard.|
|ExcludeDefTextEditor|REG_DWORD|0-1|Utilizzato per il comando di menu **Apri con.** Se non si desidera elencare l'editor di testo predefinito nell'elenco degli editor disponibili per un tipo di file specifico, impostare questo valore su 1.|
|Guida Di LinkedEditorGUID|REG_SZ|*\<>GUID*|Utilizzato per qualsiasi servizio di linguaggio in grado di aprire un file con supporto della tabella codici. Ad esempio, quando si apre un file con estensione txt utilizzando il comando **Apri con,** vengono fornite opzioni per l'utilizzo dell'editor del codice sorgente con e senza codifica.<br /><br /> Il GUID specificato nel nome della sottochiave è per la factory dell'editor di tabelle codici; il GUID collegato specificato in questa voce del Registro di sistema specifica è per la factory dell'editor regolare. Lo scopo di questa voce è che se l'IDE non apre un file utilizzando l'editor predefinito, l'IDE tenterà di utilizzare l'editor successivo nell'elenco. Il prossimo editor non dovrebbe essere la factory dell'editor di tabelle codici perché questa factory dell'editor è fondamentalmente la stessa della factory dell'editor che non è riuscita.|
|Pacchetto|REG_SZ|*\<>GUID*|GUID VSPackage per ResID del nome visualizzato.|

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

## <a name="registry-entries-for-logical-view-options"></a>Voci del Registro di sistema per le opzioni di visualizzazione logicaRegistry Entries for Logical View Options
 La\\*GUI dell'editor *di VS Reg *Root*>possibile contenere i valori seguenti.

|Nome|Type|Range|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ||Non utilizzato.|
|*\<>GUID*|REG_SZ|""|Chiave per le viste logiche supportate. Puoi averne tutti di questi di cui hai bisogno. Il nome della voce del Registro di sistema è ciò che è importante, non il valore, che è sempre una stringa vuota.|

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

## <a name="registry-entries-for-editor-extension-options"></a>Voci del Registro di sistema per le opzioni di estensione dell'editorRegistry Entries for Editor Extension Options
 La chiave *VS Reg Root*-\\*Editors Editor GUID*: Extensions può contenere i seguenti valori. L'estensione del nome file non include il punto iniziale.

|Nome|Type|Range|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ||Non utilizzato.|
|*\<ext>*|REG_DWORD|0-0xffffffff|Priorità relativa delle estensioni. Se due o più lingue condividono la stessa estensione, viene scelta la lingua con priorità più alta.|

 Inoltre, la selezione predefinita dell'utente corrente per un editor viene archiviata in HKEY_Current_User software Microsoft VisualStudio\\*X.Y*, Editor\\predefiniti*ext*. Il GUID del servizio di linguaggio selezionato si trova nella voce Custom. Questo ha la precedenza per l'utente corrente.

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

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Voci del Registro di sistema per le opzioni del servizio di linguaggio Framework dei pacchetti gestitiRegistry Entries for Managed Package Framework Language Service Options
 Le voci del Registro di sistema seguenti sono specifiche per le classi del servizio di linguaggio MPF (Managed Package Framework). Queste voci del Registro di sistema indicano il supporto nel servizio di linguaggio per varie funzionalità di IntelliSense e per altre funzionalità di modifica avanzate.

 Queste voci del Registro <xref:Microsoft.VisualStudio.Package.LanguagePreferences> di sistema sono accessibili tramite la classe .

|Nome|Type|Range|Descrizione|
|----------|----------|-----------|-----------------|
|CodeSense|REG_DWORD|0-1|Supporto per le operazioni IntelliSense.Support for IntelliSense operations.|
|Parentesi corrispondenti|REG_DWORD|0-1|Supporto per coppie di lingue corrispondenti, ad esempio parentesi graffe, parentesi e parentesi quadre.|
|Informazioni rapide|REG_DWORD|0-1|Supporto per l'operazione di informazioni rapide di IntelliSense.Support for the IntelliSense Quick Info operation.|
|ShowMatchingBrace|REG_DWORD|0-1|Supporto per la visualizzazione della coppia di lingue corrispondenti nella barra di stato.|
|MatchBracesAtCaret|REG_DWORD|0-1|Supporto per la visualizzazione di coppie di lingue corrispondenti, in genere tramite l'evidenziazione dei due elementi.|
|MaxErrorMessages|REG_DWORD|0-n|Numero massimo di errori che possono essere visualizzati nella finestra **Elenco errori.**|
|CodeSenseDelay|REG_DWORD|0-n|Numero di millisecondi di ritardo prima dell'avvio di qualsiasi analisi in background per un'operazione IntelliSense.|
|EnableAsyncCompletion (Completamento asincrono)|REG_DWORD|0-1|Supporto per l'analisi in background.|
|EnableCommenting (Commento)|REG_DWORD|0-1|Il supporto per l'aggiunta di commenti a blocchi di testo selezionati e implica anche il supporto per la rimuovi commentazione del testo selezionato.|
|EnableFormatSelection (Selezionedi EnableFormatSelection)|REG_DWORD|0-1|Supporto per la formattazione del testo, ad esempio il rientro automatico o la regolazione della posizione delle parentesi graffe.|
|Ritaglio automatico|REG_DWORD|0-1|Supporto per la struttura (aree che possono essere compresse).|
|MaxRegioni|REG_DWORD|0-n|Numero massimo di aree nascoste per file.|

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
- [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)
