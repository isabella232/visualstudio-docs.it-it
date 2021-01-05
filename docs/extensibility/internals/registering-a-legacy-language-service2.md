---
title: Registrazione di un Service2 di linguaggio legacy | Microsoft Docs
description: Questo articolo elenca le voci del registro di sistema per le varie opzioni di servizio di linguaggio disponibili in Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 08b9e88440fcb7b488e479e4188279d82a526e4c
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875180"
---
# <a name="registering-a-legacy-language-service-2"></a>Registrazione di un servizio di linguaggio Legacy 2
Le sezioni seguenti forniscono elenchi di voci del registro di sistema per le varie opzioni di servizio di linguaggio disponibili in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Nel seguente elenco di voci del registro di sistema, *vs reg root* è uguale a HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *x. y*, dove *x. y* è il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] numero di versione.

## <a name="registry-entries-for-language-service-options"></a>Voci del registro di sistema per le opzioni del servizio di linguaggio
 La chiave del nome della lingua dei servizi \Languages\Language di *Visual Studio reg* \\  può contenere i valori seguenti.

|Nome|Tipo|Range|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ|*\<GUID>*|GUID del servizio di linguaggio.|
|LangResID|REG_DWORD|0x0-0xFFFF|Identificatore di risorsa di stringa (da un Resid) per il nome di testo localizzato della lingua.|
|Pacchetto|REG_SZ|*\<GUID>*|GUID del pacchetto VSPackage.|
|ShowCompletion|REG_DWORD|0-1|Specifica se sono abilitate le opzioni di **completamento istruzioni** nella finestra di dialogo **Opzioni** .|
|ShowSmartIndent|REG_DWORD|0-1|Specifica se l'opzione per selezionare rientri **intelligenti** nella finestra di dialogo **Opzioni** è abilitata.|
|RequestStockColors|REG_DWORD|0-1|Specifica se i colori personalizzati o predefiniti vengono utilizzati per colorare le parole chiave.|
|ShowHotURLs|REG_DWORD|0-1|Specifica se l'utente può fare clic su URL.|
|Impostazione predefinita su URL non sensibili|REG_DWORD|0-1|Consente di specificare l'impostazione iniziale per l'opzione di **spostamento URL con clic singolo** nella finestra di dialogo **Opzioni** .|
|DefaultToInsertSpaces|REG_DWORD|0-1|Specifica se il servizio di linguaggio ha "Inserisci spazi" come opzione di scheda predefinita.|
|ShowDropdownBarOption|REG_DWORD|0-1|Abilita o Disabilita l'opzione **barra di navigazione** nella finestra di dialogo **Opzioni** che Mostra o nasconde la barra di **spostamento**.|
|Solo finestra del codice singolo|REG_DWORD|0-1|Abilita o Disabilita la nuova scelta della **finestra** nel menu **finestra** per un servizio di linguaggio.|
|EnableAdvancedMembersOption|REG_DWORD|0-1|Abilita o disabilita un'impostazione della finestra di dialogo **Opzioni** per **Nascondi membri avanzati**.|
|Supporto CF_HTML|REG_DWORD|0-1|Specifica se l'editor consente di copiare e incollare i dati HTML.|
|EnableLineNumbersOption|REG_DWORD|0-1|Specifica se le opzioni dei **numeri di riga** nella finestra di dialogo **Opzioni** sono abilitate per un servizio di linguaggio.|
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Specifica se i membri avanzati, ad esempio i campi privati, sono nascosti negli elenchi di completamento.|
|ShowBraceCompletion|REG_DWORD|0-1|Specifica se l'opzione di **completamento della parentesi graffa** nella finestra di dialogo **Opzioni** è abilitata.|

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

## <a name="registry-entries-for-debugger-languages-options"></a>Voci del registro di sistema per le opzioni dei linguaggi del debugger
 Il nome della lingua dei servizi \Languages\Language di *vs reg radice* \\ \Debugger lingue \\ *GUID*\ chiave può includere i valori seguenti.

|Nome|Tipo|Range|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ|text|Il valore predefinito può essere utilizzato per documentare il nome della lingua. Il nome di questa chiave è un GUID di un analizzatore di espressioni con una voce corrispondente nell' *\<VS Reg Root>* analizzatore di \AD7Metrics\Expression.|

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

## <a name="registry-entries-for-editor-tools-options"></a>Voci del registro di sistema per le opzioni degli strumenti dell'editor
 È possibile aggiungere chiavi del registro di sistema nella chiave EditorToolsOptions per le pagine delle proprietà e i nodi delle proprietà. Queste chiavi e i rispettivi valori identificano le pagine delle proprietà nella finestra di dialogo **Opzioni** (nel menu **strumenti** ) utilizzate per configurare il servizio di linguaggio. Nell'esempio seguente il nome della *pagina* è il nome di una pagina delle proprietà e il nome del *nodo* è il nome di un nodo nell'albero della finestra di dialogo **Opzioni** . La voce di pagina e la voce del nodo devono essere specificate separatamente.

|Nome|Tipo|Range|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ|Da un Resid|Nome visualizzato localizzato della pagina di opzioni. Il nome può essere un testo letterale o # `nnn` , dove `nnn` è un ID di risorsa stringa nella DLL satellite del pacchetto VSPackage specificato.|
|Pacchetto|REG_SZ|*GUID*|GUID del pacchetto VSPackage che implementa questa pagina di opzioni.|
|Pagina|REG_SZ|*GUID*|GUID della pagina delle proprietà da richiedere dal pacchetto VSPackage chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metodo. Se questa voce del registro di sistema non è presente, la chiave del registro di sistema descrive un nodo, non una pagina.|

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

## <a name="registry-entries-for-file-name-extension-options"></a>Voci del registro di sistema per le opzioni di estensione di file
 La voce per l'estensione di file deve includere il periodo principale, ad esempio ". myext".

|Nome|Tipo|Range|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ|*GUID*|GUID del servizio per il servizio di linguaggio predefinito per questo tipo di estensione del nome di file.|

### <a name="example"></a>Esempio

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>Voci del registro di sistema per le opzioni dell'editor
 La chiave \Editors *radice di vs reg* può contenere i valori seguenti:

|Nome|Tipo|Range|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ|""|Inutilizzati qui è possibile inserire il nome per la documentazione.|
|DefaultToolboxTab|REG_SZ|""|Nome della scheda della casella degli strumenti da rendere predefinita quando l'editor è attivo.|
|DisplayName|REG_SZ|Da un Resid|Nome da visualizzare nella finestra di dialogo **Apri con** . Il nome è l'ID risorsa stringa o un nome in formato standard.|
|ExcludeDefTextEditor|REG_DWORD|0-1|Usato per il comando di menu **Apri con** . Se non si desidera elencare l'editor di testo predefinito nell'elenco di editor disponibili per un tipo di file specifico, impostare questo valore su 1.|
|LinkedEditorGUID|REG_SZ|*\<GUID>*|Utilizzato per qualsiasi servizio di linguaggio in grado di aprire un file con supporto della tabella codici. Ad esempio, quando si apre un file con estensione txt usando il comando **Apri con** , vengono fornite le opzioni per l'uso dell'editor del codice sorgente con e senza codifica.<br /><br /> Il GUID specificato nel nome della sottochiave è per la factory dell'editor CodePage. il GUID collegato specificato in questa specifica voce del registro di sistema è relativo alla factory dell'editor normale. Lo scopo di questa voce è che se l'IDE non apre un file con l'editor predefinito, l'IDE tenterà di usare l'editor successivo nell'elenco. Questo editor successivo non dovrebbe essere la factory dell'editor codepage perché questa factory dell'editor è fondamentalmente identica alla factory dell'editor che ha avuto esito negativo.|
|Pacchetto|REG_SZ|*\<GUID>*|GUID VSPackage per il nome visualizzato da un Resid.|

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

## <a name="registry-entries-for-logical-view-options"></a>Voci del registro di sistema per le opzioni di visualizzazione logica
 L'interfaccia utente grafica dell'editor \Editors di *vs reg radice* \\ *>* chiave \LogicalViews può contenere i valori seguenti.

|Nome|Tipo|Range|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ||Non utilizzato.|
|*\<GUID>*|REG_SZ|""|Chiave per le visualizzazioni logiche supportate. È possibile disporre di tutti gli altri necessari. Il nome della voce del registro di sistema è quello che è importante, non il valore, che è sempre una stringa vuota.|

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

## <a name="registry-entries-for-editor-extension-options"></a>Voci del registro di sistema per le opzioni di estensione dell'editor
 La chiave \Extensions GUID dell'editor \Editors di *vs reg radice* \\ può contenere i valori seguenti. L'estensione del nome file non include il punto iniziali.

|Nome|Tipo|Range|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ||Non utilizzato.|
|*\<ext>*|REG_DWORD|0-0xFFFFFFFF|Priorità relativa delle estensioni. Se due o più lingue condividono la stessa estensione, viene scelta la lingua con priorità più alta.|

 Inoltre, la selezione predefinita dell'utente corrente per un editor è archiviata in HKEY_Current_User \Software\Microsoft\VisualStudio \\ *X. Y*\Default Editors \\ *ext*. Il GUID del servizio di linguaggio selezionato si trova nella voce personalizzata. Questa operazione ha la precedenza sull'utente corrente.

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

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Voci del registro di sistema per le opzioni del servizio di linguaggio Managed Package Framework
 Le seguenti voci del registro di sistema sono specifiche per le classi del servizio di linguaggio MPF (Managed Package Framework). Queste voci del registro di sistema indicano il supporto nel servizio di linguaggio per varie funzionalità di IntelliSense e per altre funzionalità di modifica avanzate.

 È possibile accedere a queste voci del registro di sistema tramite la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.

|Nome|Tipo|Range|Descrizione|
|----------|----------|-----------|-----------------|
|CodeSense|REG_DWORD|0-1|Supporto per le operazioni di IntelliSense.|
|MatchBraces|REG_DWORD|0-1|Supporto per coppie di lingue corrispondenti, ad esempio parentesi graffe, parentesi e parentesi quadre.|
|Informazioni rapide|REG_DWORD|0-1|Supporto per l'operazione di informazioni rapide di IntelliSense.|
|ShowMatchingBrace|REG_DWORD|0-1|Supporto per la visualizzazione della coppia di lingue corrispondenti nella barra di stato.|
|MatchBracesAtCaret|REG_DWORD|0-1|Supporto per la visualizzazione di coppie di lingue corrispondenti, in genere tramite l'evidenziazione dei due elementi.|
|MaxErrorMessages|REG_DWORD|0-n|Numero massimo di errori che possono essere visualizzati nella finestra **Elenco errori** .|
|CodeSenseDelay|REG_DWORD|0-n|Numero di millisecondi di ritardo prima dell'avvio di un'analisi in background per un'operazione di IntelliSense.|
|EnableAsyncCompletion|REG_DWORD|0-1|Supporto per l'analisi in background.|
|EnableCommenting|REG_DWORD|0-1|Supporto per impostare come commento i blocchi di testo selezionati e implica anche il supporto per rimuovere il commento dal testo selezionato.|
|EnableFormatSelection|REG_DWORD|0-1|Supporto per la formattazione di testo, ad esempio il rientro automatico o la regolazione della posizione delle parentesi graffe.|
|AutoOutlining|REG_DWORD|0-1|Supporto per la struttura (aree che possono essere compresse).|
|MaxRegions|REG_DWORD|0-n|Numero massimo di aree nascoste per ogni file.|

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

## <a name="see-also"></a>Vedi anche
- [Sviluppo di un servizio di linguaggio legacy](../../extensibility/internals/developing-a-legacy-language-service.md)
