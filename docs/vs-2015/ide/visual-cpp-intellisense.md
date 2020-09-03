---
title: Intellisense per Visual C++ |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 9d7c6414-4e6c-4889-a74c-a6033795eccc
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 173020a95977bdae2ad3006ce23dea376fb9d22e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72608816"
---
# <a name="visual-c-intellisense"></a>IntelliSense per Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio 2015 IntelliSense è disponibile per singoli file del codice e per i file nei progetti. Nei progetti multipiattaforma alcune funzionalità di IntelliSense sono disponibili nel file con estensione cpp e c del progetto di codice condiviso anche quando si opera in un contesto Android o iOS.

## <a name="intellisense-features-in-c"></a>Funzionalità IntelliSense in C++
 IntelliSense è un nome assegnato a un set di funzionalità che semplificano la scrittura di codice. Per una maggiore flessibilità, tutte le funzionalità di IntelliSense possono essere abilitate o disabilitate nella pagina delle proprietà accessibile tramite **Editor di testo, C/C++, Avanzate**.

 ![Strumenti, opzioni, editor di testo, C&#47;C&#43;&#43;, avanzate](../ide/media/sintellisensecpptoolsoptions.PNG "sIntelliSenseCppToolsOptions")

 Per accedere a IntelliSense, è possibile utilizzare le voci di menu e i tasti di scelta rapida illustrati nella figura seguente.

 ![Menu IntelliSense di Visual C&#43;&#43; ](../ide/media/vs2015-cpp-intellisense-menu.png "vs2015_cpp_intellisense_menu")

### <a name="statement-completion-and-member-list"></a>Elenco di completamento istruzioni e dei membri
 Quando si inizia a digitare una parola chiave, un tipo, una funzione, un nome di variabile o un altro elemento del programma che viene riconosciuto dal compilatore, l'editor visualizza un elenco di suggerimenti per completare la parola.

 Per un elenco delle icone e dei relativi significati, vedere [Icone di Visualizzazione classi e Visualizzatore oggetti](../ide/class-view-and-object-browser-icons.md).

 ![Finestra di Word completa di Visual C&#43;&#43; ](../ide/media/vs2015-cpp-complete-word.png "vs2015_cpp_complete_word")

 La prima volta che viene richiamato, l'elenco dei membri mostra solo i membri accessibili per il contesto corrente. Se successivamente si usa **CTRL+J**, vengono visualizzati tutti i membri indipendentemente dall'accessibilità. Se viene richiamato per la terza volta, viene visualizzato un elenco di elementi del programma ancora più ampio. È possibile disattivare il completamento delle istruzioni nella pagina **Opzioni generali di C/C++** .

 ![Elenco dei membri di Visual C&#43;&#43; ](../ide/media/vs2015-cpp-list-members.png "vs2015_cpp_list_members")

### <a name="parameter-help"></a>Guida per i parametri
 Quando si digita una parentesi graffa di apertura di una chiamata di funzione o una parentesi angolare in una dichiarazione di variabile del modello di classe, l'editor visualizza una piccola finestra con i tipi di parametro per ogni overload del costruttore o della funzione. Il parametro corrente, sulla base della posizione del cursore, è visualizzato in grassetto. È possibile disattivare il completamento delle istruzioni nella pagina **Opzioni generali di C/C++**.

 ![Guida per i parametri di Visual C&#43;&#43; ](../ide/media/vs-2015-cpp-param-help.png "vs_2015_cpp_param_help")

### <a name="quick-info"></a>Informazioni rapide
 Quando si passa con il cursore del mouse su una variabile, viene visualizzata una piccola finestra inline che mostra le informazioni sul tipo e l'intestazione in cui è definito il tipo. Passare con il puntatore del mouse su una chiamata di funzione per visualizzare la firma della funzione. È possibile disattivare la funzionalità Informazioni rapide nella pagina **Editor di testo, C/C++, Avanzate**.

 ![Visual C&#43;&#43; informazioni rapide](../ide/media/vs2015-cpp-quickinfo.png "vs2015_cpp_quickInfo")

## <a name="error-squiggles"></a>Sottolineatura a zigzag per gli errori
 La presenza di una sottolineatura a zigzag sotto un elemento di programma (variabile, parola chiave, parentesi, nome di tipo e così via) serve a richiamare l'attenzione su un errore effettivo o potenziale nel codice. La sottolineatura a zigzag di colore verde appare quando si scrive una dichiarazione con prototipo per ricordare che non è ancora stata scritta l'implementazione. La sottolineatura a zigzag di colore viola appare in un progetto condiviso quando è presente un errore in codice attualmente non attivo, ad esempio quando si lavora nel contesto Windows ma si scrive codice errato in un contesto Android. La sottolineatura a zigzag di colore rosso indica che nel codice attivo è presente un errore o un avviso che è necessario risolvere.

 ![Errore di&#43;&#43; di Visual C controllo ortografia durante](../ide/media/vs2015-cpp-error-quiggles.png "vs2015_cpp_error_quiggles")

## <a name="code-colorization-and-fonts"></a>Tipi di carattere e colori del codice
 I colori e i tipi di carattere predefiniti possono essere modificati nella pagina delle proprietà **Ambiente, Tipi di carattere e colori**. In questa pagina è possibile modificare i tipi di carattere per molte finestre dell'interfaccia utente, non solo per l'editor. Le impostazioni specifiche di C++ iniziano con "C++", mentre le altre impostazioni sono valide per tutti i linguaggi.

## <a name="cross-platform-intellisense"></a>IntelliSense multipiattaforma
 In un progetto di codice condiviso, alcune funzionalità di IntelliSense come la sottolineatura a zigzag sono disponibili anche quando si lavora in un contesto Android. Se si scrive codice che causa un errore in un progetto inattivo, IntelliSense mostra comunque la sottolineatura a zigzag, ma in un colore diverso rispetto a quello della sottolineatura a zigzag per gli errori nel contesto corrente.

 Di seguito un'applicazione OpenGLES configurata per la compilazione per Android e iOS. Nell’illustrazione viene mostrato il codice condiviso modificato. Nella prima immagine, Android è il progetto attivo:

 ![Il progetto Android è il progetto attivo.](../ide/media/intellisensecppcrossplatform.png "IntelliSenseCppCrossPlatform")

 Tenere presente quanto segue:

- Il ramo #else sulla riga 8 è disattivato per indicare l'area inattiva, perché `__ANDROID__` è definito per il progetto Android.

- La variabile di saluto sulla riga 11 viene inizializzata con l’identificatore HELLO, che ha una sottolineatura a zig-zag di colore viola. Ciò è dovuto al fatto che nessun identificatore HELLO è definito nel progetto iOS attualmente inattivo. Mentre nel progetto Android la riga 11 verrebbe compilata, non funzionerebbe in iOS. Poiché si tratta di codice condiviso, elemento che è necessario modificare anche se viene compilato nella configurazione attualmente attiva.

- La riga 12 ha una sottolineatura rossa a zig-zag sull'identificatore BYE; tale identificatore non è definito nel progetto attivo correntemente selezionato.

  A questo punto, impostare il progetto attivo su iOS.StaticLibrary e osservare come cambiano le sottolineature a zig-zag.

  ![iOS è selezionato come progetto attivo.](../ide/media/intellisensecppcrossplatform2.png "IntelliSenseCppCrossPlatform2")

  Tenere presente quanto segue:

- Il ramo #ifdef alla riga 6 è disattivato per indicare l'area inattiva, perché *_ANDROID \\ * \_ non è definito per il progetto iOS.

- La variabile di saluto sulla riga 11 viene inizializzata con l’identificatore HELLO, che ora ha una sottolineatura a zig-zag di colore rosso. Ciò è dovuto al fatto che nessun identificatore HELLO è definito nel progetto iOS attualmente attivo.

- La riga 12 ha una sottolineatura a zig-zag di colore viola sull’identificatore BYE; tale identificatore non è definito nel progetto Android.NativeActivity attualmente inattivo.

## <a name="single-file-intellisense"></a>IntelliSense con singolo file
 IntelliSense è disponibile anche quando si apre un singolo file all'esterno di qualsiasi progetto. Per abilitare o disabilitare particolari funzionalità, passare a **Editor di testo, C/C++, Avanzate** e attivare o disattivare le funzionalità IntelliSense. Per configurare IntelliSense per singoli file che non fanno parte di un progetto, cercare l’argomento relativo all'**uso di IntelliSense ed esplorazione dei file non di progetto** nella sezione **Avanzate**. Vedere [Presentazione guidata di Visual C++](https://msdn.microsoft.com/499cb66f-7df1-45d6-8b6b-33d94fd1f17c).

 ![IntelliSense di Visual C&#43;&#43; file singolo](../ide/media/vs2015-cpp-single-file-intellisense.png "vs2015_cpp_single_file_intellisense")

 Per impostazione predefinita, IntelliSense con singolo file utilizza solo directory di inclusione per trovare i file di intestazione. Per aggiungere altre directory, aprire il menu di scelta rapida del nodo **Soluzione** e aggiungere la directory all’elenco Esegui debug dei file di origine, come illustrato nella figura seguente:

 ![Aggiunta di un percorso a un file di intestazione.](../ide/media/intellisensedebugyourcode.jpg "IntelliSenseDebugYourCode")

## <a name="see-also"></a>Vedere anche
 [Utilizzo di IntelliSense](../ide/using-intellisense.md)
