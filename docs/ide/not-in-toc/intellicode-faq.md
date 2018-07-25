---
title: Domande e risposte su IntelliCode
ms.date: 07/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
manager: douge
author: markw-t
ms.author: mwthomas
ms.openlocfilehash: 79e18778eae231d16cf32c0fa68bcb6f5564b09d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079311"
---
# Domande frequenti su Visual Studio IntelliCode

Grazie per l'interesse dimostrato per Visual Studio IntelliCode. Questo breve documento di domande frequenti risponde ad alcune delle domande degli utenti.

## D. Che cos'è Visual Studio IntelliCode?

Nella Build 2018 Microsoft ha annunciato il rilascio di Visual Studio IntelliCode, una nuova funzionalità in grado di migliorare lo sviluppo di software tramite l'intelligenza artificiale. IntelliCode consente agli sviluppatori e ai team di scrivere codice con sicurezza, individuare i problemi più rapidamente ed eseguire revisioni del codice mirate.

È già stato illustrato in che modo IntelliCode garantisca il miglioramento del processo di sviluppo di software tramite:

- Completamento del codice con riconoscimento del contesto
- Guida per gli sviluppatori per il rispetto dei criteri e degli stili usati dal team
- Individuazione di problemi del codice difficili da trovare
- Revisioni del codice mirate, che pongono al centro dell'attenzione le aree realmente importanti

Gli sviluppatori possono cercare altre informazioni e registrarsi per ricevere le novità e le anteprime private future all'indirizzo [ https://aka.ms/intellicode ](https://aka.ms/intellicode).

## D. Cosa sono in grado di fare i clienti con Visual Studio IntelliCode?

Visual Studio IntelliCode è una gamma di funzionalità in grado di realizzare un miglioramento innovativo della produttività tramite l'impiego dell'intelligenza artificiale (AI).

Gli sviluppatori possono [scaricare un'estensione sperimentale](https://go.microsoft.com/fwlink/?linkid=872707) per Visual Studio 2017 versione 15.7 e successive. L'estensione offre:

- Una versione di IntelliSense con intelligenza artificiale in grado di suggerire l'API più idonea per l'uso da parte dello sviluppatore anziché limitarsi a visualizzare un elenco alfabetico di membri. Per visualizzare l'elenco dinamico, usa il contesto e i criteri correnti del codice dello sviluppatore.

- L'inferenza dello stile di codice e delle convenzioni di formattazione che consente di mantenere la coerenza del codice creando dinamicamente un [file con estensione editorconfig](../create-portable-custom-editor-options.md) dalla base di codici per definire gli stili e la formattazione del codice. Queste convenzioni consentono a Visual Studio di offrire correzioni automatiche dello stile e del formato per pulire il documento.

Nei prossimi mesi l'estensione verrà aggiornata con altre funzionalità.

## D. Perché l'inferenza EditorConfig aggiunge un 1 all'inizio del nome file?

Un problema noto dell'estendibilità di Visual Studio causa l'aggiunta di un 1 al nome del file con estensione editorconfig quando viene creato facendo clic con il pulsante destro del mouse e scegliendo **Aggiungi > Nuovo elemento**. I file denominati in questo modo non vengono riconosciuti dal processore di editorconfig in Visual Studio. Questo problema è stato risolto in Visual Studio 2017 versione 15.8 Preview 4. È possibile rimuovere l'1 nella finestra di dialogo **Aggiungi nuovo elemento**.

## D. Le convenzioni di EditorConfig non vengono applicate. Perché?
Questo problema si verifica in genere per due ragioni:

- Nelle versioni di Visual Studio 2017 precedenti alla 15.8 Preview 3 è necessario chiudere e riaprire tutti i documenti aperti per fare in modo che vengano applicate le convenzioni del file EditorConfig. Questo problema è stato risolto nella versione 15.8 Preview 3.
- Le convenzioni di formattazione non vengono mai visualizzate nell'**elenco errori** o nel controllo ortografia durante la digitazione del codice. È possibile tuttavia apportare correzioni usando la nuova estensione Formatta documento (CTRL+K, CTRL+D) in Visual Studio 2017 versione 15.8 Preview 3 o successive

## D. La funzione Formatta documento non corregge le convenzioni di stile. Perché?
Questo problema si verifica in genere per due ragioni:

- È possibile che non venga usato Visual Studio 2017 versione 15.8 Preview 3 o successive. È necessaria questa versione per poter usare il comando "Formatta documento" esteso per eseguire un'ulteriore pulizia del codice per il documento corrente.
- È possibile che le correzioni di stile non siano state autorizzate esplicitamente. La funzionalità estesa di correzione dei problemi delle convenzioni in Formatta documento si applica solo a un set di problemi predeterminato. È possibile modificare i problemi corretti scegliendo **Strumenti-Opzioni** in **Editor di testo > C# > Stile codice > Formattazione > Generale > Impostazioni formattazione documento (sperimentale)**. Si noti che le impostazioni predefinite non correggono alcune convenzioni di stile. È possibile acconsentire esplicitamente alle correzioni scegliendo **Strumenti > Opzioni**. Ad esempio, "Apply implicit/explicit type preferences" (Applica preferenze tipo implicito/esplicito) esegue regole di stile relative all'utilizzo di `var`.

## D. Quali convenzioni di EditorConfig Visual Studio IntelliCode è in grado di dedurre?

Poiché questa funzionalità è in fase sperimentale, non sono ancora supportate tutte le convenzioni documentate nelle [informazioni di riferimento sulle impostazioni dello stile di codice](../editorconfig-code-style-settings-reference.md).

Attualmente IntelliCode è in grado di dedurre le convenzioni seguenti:

Convenzioni di formattazione:

-   csharp_space_between_method_declaration_parameter_list_parentheses
-   csharp_space_between_method_declaration_empty_parameter_list_parentheses
-   csharp_space_between_method_call_name_and_opening_parenthesis
-   csharp_space_between_method_call_parameter_list_parentheses
-   csharp_space_between_method_call_empty_parameter_list_parentheses
-   csharp_space_after_keywords_in_control_flow_statements
-   csharp_space_between_parentheses
-   csharp_space_after_cast
-   csharp_space_after_colon_in_inheritance_clause
-   csharp_space_before_colon_in_inheritance_clause
-   csharp_space_around_binary_operators
-   csharp_indent_switch_labels
-   csharp_indent_case_contents
-   csharp_indent_case_contents_when_block
-   csharp_indent_labels
-   csharp_preserve_single_line_blocks
-   csharp_preserve_single_line_statements
-   csharp_new_line_before_open_brace
-   csharp_new_line_before_else
-   csharp_new_line_before_catch
-   csharp_new_line_before_finally
-   csharp_new_line_before_members_in_object_initializers
-   csharp_new_line_before_members_in_anonymous_types
-   csharp_new_line_between_query_expression_clauses

Convenzioni di stile
-   csharp__new_line_before_catch
-   csharp_new_line_before_else
-   csharp_new_line_before_members_in_anonymous_types
-   csharp_new_line_before_members_in_object_initializers
-   csharp_new_line_before_finally_style
-   csharp_new_line_between_query_expression_clauses
-   csharp_prefer_braces_style
-   csharp_preferred_modifier_order_style
-   csharp_prefer_simple_default_expression
-   csharp_preserve_single_line_blocks
-   csharp_space_after_cast
-   csharp_space_after_keywords_in_control_flow_statements
-   csharp_space_between_method_call_parameter_list_parentheses
-   csharp_space_between_method_declaration_parameter_list_parentheses
-   csharp_space_between_parentheses
-   csharp_style_expression_bodied_accessors
-   csharp_style_expression_bodied_constructors
-   csharp_style_expression_bodied_indexers
-   csharp_style_expression_bodied_methods
-   csharp_style_expression_bodied_operators
-   csharp_style_expression_bodied_properties
-   csharp_style_inlined_variable_declaration
-   csharp_style_pattern_local_over_anonymous_function
-   csharp_style_pattern_matching_over_as_with_null_check
-   csharp_style_var_for_built_in_types
-   csharp_style_var_when_type_is_apparent
-   dotnet_sort_system_directives_first
-   dotnet_style_explicit_tuple_names
-   dotnet_style_object_initializer
-   dotnet_style_predefined_type_for_locals_parameters_members
-   dotnet_style_predefined_type_for_member_access
-   dotnet_style_prefer_inferred_anonymous_type_member_names
-   dotnet_style_qualification_for_event
-   dotnet_style_qualification_for_field
-   dotnet_style_qualification_for_method
-   dotnet_style_qualification_for_property
-   dotnet_style_require_accessibility_modifiers

## D. Vi sono altre funzionalità disponibili per l'estensione di Visual Studio IntelliCode?

Numerose funzionalità sono attualmente oggetto di sviluppo; verranno condivise pubblicamente appena diventeranno disponibili. È possibile registrarsi per avere notizie e aggiornamenti all'indirizzo [https://aka.ms/intellicode](https://aka.ms/intellicode) per conoscere in anteprima le nuove funzionalità disponibili.

## D: Che cosa rende "IntelliSense assistito dall'intelligenza artificiale" con tecnologia IntelliCode migliore della versione normale di IntelliSense?

Con IntelliCode, l'elenco di completamento suggerisce l'API che con ogni probabilità è la più corretta per l'uso da parte dello sviluppatore, anziché limitarsi a visualizzare un semplice elenco alfabetico di membri. Per visualizzare l'elenco dinamico, IntelliSense usa il contesto del codice corrente dello sviluppatore e criteri basati su 2000 progetti open source di qualità elevata in GitHub, ognuno con oltre 100 stelle. I risultati formano un modello in grado di prevedere le chiamate API più probabili e pertinenti.

## D: Qual è la qualità dei suggerimenti di completamento IntelliCode?

I suggerimenti di IntelliCode sono stati usati internamente a Microsoft per un certo tempo e riteniamo che siano utili. In definitiva, tuttavia, la conferma dell'utilità di questi suggerimenti dovrà arrivare dagli sviluppatori che li usano durante la scrittura del codice. Invitiamo i nostri clienti a provare l'[estensione IntelliCode](https://go.microsoft.com/fwlink/?linkid=872707) di Visual Studio e a inviare commenti e suggerimenti sul funzionamento. Il modello verrà anche sottoposto a training in base ai suggerimenti scelti dai clienti e l'estensione verrà aggiornata man mano che il modello migliora.

> [!NOTE]
> Non verrà raccolto alcun codice definito dall'utente. Vedere la domanda relativa alla [privacy](#privacy).

## D. Qual è il futuro di IntelliCode?

È in corso l'analisi di un'ampia gamma di soluzioni per migliorare la produttività degli sviluppatori tramite l'intelligenza artificiale e altre tecniche avanzate. In occasione di Microsoft Build 2018 è stata offerta un'anteprima di alcuni degli scenari in cui l'intelligenza artificiale può essere d'aiuto agli sviluppatori, ma ne esistono molti altri. Il contributo degli sviluppatori che sperimentano quanto illustrato è di grande interesse. Questi sono quindi invitati a registrarsi all'indirizzo [ https://aka.ms/intellicode ](https://aka.ms/intellicode) per ricevere novità e aggiornamenti.

## D. Quanto costa?

Al momento non ci sono annunci relativi ai prezzi.

## D. Quando verrà rilasciato IntelliCode?

IntelliSense assistito dall'intelligenza artificiale di IntelliCode è attualmente nella prima fase di anteprima sperimentale. L'estensione sperimentale continuerà in futuro a essere aggiornata con nuove funzionalità. Non è disponibile alcuna pianificazione per la versione finale, ma commenti e suggerimenti da parte degli sviluppatori sono bene accetti, perché consentono di offrire la migliore esperienza possibile. È possibile ricevere novità e aggiornamenti registrandosi all'indirizzo [ https://aka.ms/intellicode ](https://aka.ms/intellicode).

## D. Questa esperienza è disponibile solo in Visual Studio e per C#?

In Build 2018 l'esperienza è stata illustrata con una codebase C# in Visual Studio 2017. IntelliCode verrà tuttavia espanso il più presto possibile a un numero maggiore di linguaggi e strumenti della famiglia Visual Studio in futuro.

## D. <a name="whynointellisense"/> Perché non riesco a visualizzare i suggerimenti IntelliCode in C#?

I suggerimenti IntelliCode vengono visualizzati nell'interfaccia utente di Visual Studio IntelliSense standard per C#. Le estensioni che eseguono l'override dell'interfaccia utente impediscono la visualizzazione dei suggerimenti IntelliCode nella parte superiore dell'elenco. È possibile verificare se sono le estensioni a provocare questo comportamento disattivandole e riprovando a usare IntelliSense.

Se in questo modo il problema non si risolve, eseguire una segnalazione tramite la funzionalità di Visual Studio [Segnala un problema](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) e indicare IntelliCode nella segnalazione.

## D. Quale versione di Visual Studio è necessaria per eseguire questa estensione?

L'estensione IntelliCode per Visual Studio è supportata in Visual Studio 2017 versione 15.7 Preview 5 e versioni successive (tutti gli SKU). L'installazione dell'estensione si interrompe con l'errore "Questa estensione non è installabile su nessuno dei prodotti attualmente installati." se non è installata la versione minima richiesta.

## D. Questa esperienza è disponibile solo in inglese?

IntelliCode è un'estensione di anteprima al momento e desideriamo prima di tutto capire quanto siano utili queste funzionalità per un ampio gruppo di clienti. Quando decideremo di uscire dalla versione di anteprima per IntelliCode, verranno senz'altro valutate le impostazioni locali o le lingue da supportare per prime, oltre alle caratteristiche del pacchetto, in base ai commenti e ai suggerimenti dei clienti.

## <a name="privacy"/> D: E dal punto di vista della privacy? Il codice viene inviato nel cloud? Quali dati dei clienti vengono inviati a Microsoft?

Gli sviluppatori sono invitati a provare Visual Studio IntelliCode fin da oggi come estensione di anteprima sperimentale. Lo scopo dell'estensione è di consentire agli sviluppatori di provare le funzionalità di IntelliCode e inviare commenti e suggerimenti al team del prodotto.

Per favorire il miglioramento del prodotto, vengono acquisiti in forma anonima alcuni dati sull'utilizzo e sugli errori. A Microsoft non viene inviato codice scritto dagli utenti, ma vengono raccolte informazioni sull'uso dei risultati di IntelliCode. I dati includono solo tipi e membri open source e .NET selezionati dagli utenti dall'elenco di suggerimenti di IntelliCode. Gli sviluppatori possono rifiutare esplicitamente il programma [Analisi utilizzo software di Visual Studio](../../ide/visual-studio-experience-improvement-program.md). In questo caso viene disattivata anche la raccolta dei dati per l'estensione IntelliCode. Dalla barra dei menu selezionare **?** > **Invia feedback** > **Impostazioni**. Nella finestra di dialogo **Analisi utilizzo software di Visual Studio** selezionare **No, non voglio partecipare** e quindi selezionare **OK**.

L'estensione IntelliCode può periodicamente chiedere allo sviluppatore di completare un sondaggio, anche questo anonimo. Gli utenti possono registrarsi per ricevere novità e un'anteprima privata futura, ma attualmente per usare l'estensione sperimentale non è necessario eseguire questa operazione.

Le funzionalità future potranno richiedere l'accesso a un servizio per il quale sia necessaria la registrazione. Altri dettagli verranno pubblicati quando tali funzionalità saranno pronte per l'anteprima privata.
