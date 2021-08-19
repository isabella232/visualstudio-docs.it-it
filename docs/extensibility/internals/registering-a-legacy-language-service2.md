---
title: Registrazione di un servizio di linguaggio legacy2 | Microsoft Docs
description: Questo articolo elenca le voci del Registro di sistema per le varie opzioni del servizio di linguaggio disponibili in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d33ce0af87df2e3d6506fef48aeb91f1b9ebdeef
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062951"
---
# <a name="registering-a-legacy-language-service-2"></a>Registrazione di un servizio di linguaggio legacy 2
Le sezioni seguenti forniscono elenchi di voci del Registro di sistema per le varie opzioni del servizio di linguaggio disponibili in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Nell'elenco seguente delle voci del Registro di sistema, *VS Reg Root* è uguale HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *X.Y*, dove *X.Y* è il numero [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di versione.

## <a name="registry-entries-for-language-service-options"></a>Voci del Registro di sistema per le opzioni del servizio di linguaggio
 La *chiave VS Reg Root*\Languages\Language Services Language \\ *Name* può contenere i valori seguenti.

|Nome|Tipo|Intervallo|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ|*\<GUID>*|GUID del servizio di linguaggio.|
|LangResID|REG_DWORD|0x0-0xffff|Identificatore di risorsa stringa (ResID) per il nome del testo localizzato della lingua.|
|Pacchetto|REG_SZ|*\<GUID>*|GUID del pacchetto VSPackage.|
|ShowCompletion|REG_DWORD|0-1|Specifica se le opzioni **Completamento istruzione** nella finestra **di dialogo** Opzioni sono abilitate.|
|ShowSmartIndent|REG_DWORD|0-1|Specifica se l'opzione per selezionare **Rientro** intelligente nella finestra **di** dialogo Opzioni è abilitata.|
|RequestStockColors|REG_DWORD|0-1|Specifica se i colori personalizzati o predefiniti vengono usati per colorare le parole chiave.|
|ShowHotURLs|REG_DWORD|0-1|Specifica se l'utente può fare clic su URL.|
|Impostazione predefinita su URL non hot|REG_DWORD|0-1|Specifica l'impostazione iniziale per l'opzione **Abilita navigazione URL** a singolo clic nella finestra di **dialogo** Opzioni .|
|DefaultToInsertSpaces|REG_DWORD|0-1|Specifica se il servizio di linguaggio dispone di "spazi di inserimento" come opzione di tabulazione predefinita.|
|ShowDropdownBarOption|REG_DWORD|0-1|Abilita o disabilita **l'opzione Barra di** spostamento nella finestra **di** dialogo Opzioni che mostra o nasconde la barra **di spostamento**.|
|Solo finestra del codice singolo|REG_DWORD|0-1|Abilita o disabilita la scelta **Nuova finestra** nel menu **Finestra** per un servizio di linguaggio.|
|EnableAdvancedMembersOption|REG_DWORD|0-1|Abilita o disabilita **un'impostazione della finestra** di dialogo Opzioni per Nascondi membri **avanzati**.|
|Supporto CF_HTML|REG_DWORD|0-1|Specifica se l'editor consente di copiare e incollare dati HTML.|
|EnableLineNumbersOption|REG_DWORD|0-1|Specifica se le opzioni **Numeri di** riga nella finestra di **dialogo Opzioni** sono abilitate per un servizio di linguaggio.|
|HideAdvancedMembersByDefault|REG_DWORD|0-1|Specifica se i membri avanzati, ad esempio i campi privati, sono nascosti negli elenchi di completamento.|
|ShowBraceCompletion|REG_DWORD|0-1|Specifica se **l'opzione Completamento parentesi graffe** nella **finestra di** dialogo Opzioni è abilitata.|

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

## <a name="registry-entries-for-debugger-languages-options"></a>Voci del Registro di sistema per le opzioni dei linguaggi del debugger
 La *chiave RADICE DI VISUAL STUDIO Reg*\Languages\Language Services Language \\ *Name*\Debugger Languages \\ *GUID*\ può includere i valori seguenti.

|Nome|Tipo|Intervallo|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ|text|Il valore predefinito può essere usato per documentare il nome della lingua. Il nome di questa chiave è un GUID di un analizzatore di espressioni con una voce corrispondente in *\<VS Reg Root>* \AD7Metrics\Expression Evaluator.|

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

## <a name="registry-entries-for-editor-tools-options"></a>Voci del Registro di sistema per le opzioni degli strumenti dell'editor
 È possibile aggiungere chiavi del Registro di sistema nella chiave EditorToolsOptions per le pagine delle proprietà e i nodi delle proprietà. Queste chiavi e i relativi  valori identificano le pagine delle proprietà nella finestra di dialogo Opzioni **(nel** menu Strumenti) usate per configurare il servizio di linguaggio. Nell'esempio seguente *Nome* pagina è il nome  di una pagina delle proprietà e Nome nodo è il nome di un nodo nell'albero della finestra **di dialogo** Opzioni . La voce di pagina e la voce del nodo devono essere specificate separatamente.

|Nome|Tipo|Intervallo|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ|Resid|Nome visualizzato localizzato di questa pagina delle opzioni. Il nome può essere un testo letterale o # , dove è un ID risorsa stringa nella `nnn` DLL satellite del pacchetto `nnn` VSPackage specificato.|
|Pacchetto|REG_SZ|*GUID*|GUID del pacchetto VSPackage che implementa questa pagina di opzioni.|
|Pagina|REG_SZ|*GUID*|GUID della pagina delle proprietà da richiedere dal pacchetto VSPackage chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metodo . Se questa voce del Registro di sistema non è presente, la chiave del Registro di sistema descrive un nodo, non una pagina.|

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

## <a name="registry-entries-for-file-name-extension-options"></a>Voci del Registro di sistema per le opzioni dell'estensione file
 La voce per l'estensione di file deve includere il punto iniziale, ad esempio ".myext".

|Nome|Tipo|Intervallo|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ|*GUID*|GUID del servizio per il servizio di linguaggio predefinito per questo tipo di estensione di file.|

### <a name="example"></a>Esempio

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>Voci del Registro di sistema per le opzioni dell'editor
 La *chiave \Editors radice* di VS Reg può contenere i valori seguenti:

|Nome|Tipo|Intervallo|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ|""|Non usato; È possibile inserire il proprio nome qui per la documentazione.|
|DefaultToolboxTab|REG_SZ|""|Nome della scheda della casella degli strumenti da impostare come predefinito quando l'editor è attivo.|
|DisplayName|REG_SZ|Resid|Nome da visualizzare nella **finestra di dialogo** Apri con . Il nome è l'ID risorsa stringa o un nome in formato standard.|
|ExcludeDefTextEditor|REG_DWORD|0-1|Usato per il **comando di** menu Apri con. Se non si vuole elencare l'editor di testo predefinito nell'elenco degli editor disponibili per un tipo di file specifico, impostare questo valore su 1.|
|LinkedEditorGUID|REG_SZ|*\<GUID>*|Usato per qualsiasi servizio di linguaggio in grado di aprire un file con il supporto della tabella codici. Ad esempio, quando si apre un file  .txt usando il comando Apri con , vengono fornite opzioni per l'uso dell'editor del codice sorgente con e senza codifica.<br /><br /> Il GUID specificato nel nome della sottochiave è per la factory dell'editor della tabella codici. il GUID collegato specificato in questa voce del Registro di sistema specifica è per la normale factory dell'editor. Lo scopo di questa voce è che se l'IDE non apre un file usando l'editor predefinito, l'IDE tenterà di usare l'editor successivo nell'elenco. Questo editor successivo non deve essere la factory dell'editor della tabella codici perché questa factory dell'editor è fondamentalmente la stessa della factory dell'editor che ha avuto esito negativo.|
|Pacchetto|REG_SZ|*\<GUID>*|GUID del pacchetto VSPackage per il ResID del nome visualizzato.|

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
 *L'interfaccia utente* grafica dell'editor di Visual Studio Reg \\ *Root \Editors>* \LogicalViews può contenere i valori seguenti.

|Nome|Tipo|Intervallo|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ||Non utilizzato.|
|*\<GUID>*|REG_SZ|""|Chiave per le viste logiche supportate. È possibile avere tutti questi elementi necessari. Il nome della voce del Registro di sistema è importante, non il valore, che è sempre una stringa vuota.|

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

## <a name="registry-entries-for-editor-extension-options"></a>Voci del Registro di sistema per le opzioni di estensione dell'editor
 La *chiave VS Reg Root*\Editors Editor \\ *GUID*\Extensions può contenere i valori seguenti. L'estensione del nome file non include il punto iniziale.

|Nome|Tipo|Intervallo|Descrizione|
|----------|----------|-----------|-----------------|
|Valore predefinito.|REG_SZ||Non utilizzato.|
|*\<ext>*|REG_DWORD|0-0xffffffff|Priorità relativa delle estensioni. Se due o più lingue condividono la stessa estensione, viene scelta la lingua con priorità più alta.|

 Inoltre, la selezione predefinita dell'utente corrente per un editor viene archiviata in HKEY_Current_User\Software\Microsoft\VisualStudio \\ *X.Y*\Default Editors \\ *ext*. Il GUID del servizio di linguaggio selezionato si trova nella voce Personalizzata. Ha la precedenza per l'utente corrente.

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

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Voci del Registro di sistema per le opzioni del servizio di linguaggio managed package framework
 Le voci del Registro di sistema seguenti sono specifiche delle classi del servizio di linguaggio MPF (Managed Package Framework). Queste voci del Registro di sistema indicano il supporto nel servizio di linguaggio per varie funzionalità di IntelliSense e per altre funzionalità di modifica avanzate.

 Queste voci del Registro di sistema sono accessibili tramite la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe .

|Nome|Tipo|Intervallo|Descrizione|
|----------|----------|-----------|-----------------|
|CodeSense|REG_DWORD|0-1|Supporto per le operazioni IntelliSense.|
|MatchBraces|REG_DWORD|0-1|Supporto per la corrispondenza di coppie di linguaggi, ad esempio parentesi graffe, parentesi e parentesi quadre.|
|Informazioni rapide|REG_DWORD|0-1|Supporto per l'operazione informazioni rapide di IntelliSense.|
|ShowMatchingBrace|REG_DWORD|0-1|Supporto per la visualizzazione della coppia di lingue corrispondente nella barra di stato.|
|MatchBracesAtCaret|REG_DWORD|0-1|Supporto per la visualizzazione di coppie di lingue corrispondenti, in genere tramite l'evidenziazione dei due elementi.|
|MaxErrorMessages|REG_DWORD|0-n|Numero massimo di errori che possono essere visualizzati nella **finestra Elenco** errori.|
|CodeSenseDelay|REG_DWORD|0-n|Numero di millisecondi di ritardo prima dell'avvio di qualsiasi analisi in background per un'operazione IntelliSense.|
|EnableAsyncCompletion|REG_DWORD|0-1|Supporto per l'analisi in background.|
|EnableCommenting|REG_DWORD|0-1|Il supporto per impostare come commento i blocchi di testo selezionati e implica anche il supporto per rimuovere il commento del testo selezionato.|
|EnableFormatSelection|REG_DWORD|0-1|Supporto per la formattazione del testo, ad esempio il rientro automatico o la modifica della posizione delle parentesi graffe.|
|Strutturazione automatica|REG_DWORD|0-1|Supporto per la struttura (aree che possono essere compresse).|
|MaxRegions|REG_DWORD|0-n|Numero massimo di aree nascoste per file.|

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
