---
title: Modifiche supportate al codice (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue, limitations
- supported code changes
- object files, limitations of Edit and Continue
- C++ language, supported code changes
- coding, supported code changes
- resource files, limitations of Edit and Continue
- code changes, handling in Edit and Continue
- what's new [C++], supported code changes
- code changes
ms.assetid: f5754363-8a56-417b-b904-b05d9dd26d03
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f167b3e9d27145284defa2ff491bb9ce0085f2a3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65684905"
---
# <a name="supported-code-changes-c"></a>Modifiche al codice supportate (C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'opzione Modifica e continuazione per Visual C++ gestisce la gran parte dei tipi di modifica al codice. Alcune modifiche non possono tuttavia essere applicate durante l'esecuzione del programma. Per applicare tali modifiche, è necessario arrestare l'esecuzione e compilare una versione aggiornata del codice.  
  
 Vedere [Edit and Continue (Visual C++)](../debugger/edit-and-continue-visual-cpp.md) per informazioni sull'uso di Modifica e continuazione per C++ in Visual Studio.  
  
## <a name="BKMK_Unsupported_changes"></a> Modifiche non supportate  

Le seguenti modifiche del codice C/C++ non possono essere applicate durante una sessione di debug:  
  
- La maggior parte delle modifiche a dati globali o statici.  
  
- Le modifiche a file eseguibili copiati da un altro computer e non compilati localmente.  
  
- Le modifiche a un tipo di dati che hanno effetto sul layout di un oggetto, ad esempio i membri dati di una classe.  
  
- Aggiunta di più di 64 KB di nuovo codice o nuovi dati.  
  
- Aggiunta di variabili che richiedono un costruttore in un punto precedente al puntatore all'istruzione.  
  
- Modifiche che interessano il codice per il quale è necessaria l'inizializzazione di runtime.  
  
- Aggiunta di gestori di eccezioni, in alcune istanze.  
  
- Modifiche di file di risorse.  
  
- Modifiche del codice di file di sola lettura.  
  
- Modifiche del codice privo di un file PDB corrispondente.  
  
- Modifiche del codice privo di un file oggetto.  
  
Se si apporta una di queste modifiche e si tenta quindi di applicare le modifiche al codice, viene visualizzato un messaggio di errore o di avviso nella finestra **Output** .  
  
- Le librerie statiche non vengono aggiornate con la funzionalità Modifica e continuazione. Se si apporta una modifica in una libreria statica, l'esecuzione continua con la versione precedente e non viene visualizzato alcun avviso.  
  
## <a name="BKMK_Unsupported_scenarios"></a> Scenari non supportati  
 Modifica e continuazione per C/C++ non è disponibile nei seguenti scenari di debug:  
  
- Debug di applicazioni native compilate con [/Zo (Ottimizzare il debug)](https://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f)  
  
- Nelle versioni di Visual Studio precedenti a Visual Studio 2015 Update 1, debug di app di Windows Store o componenti. A partire da Visual Studio 2015 Update 1, è possibile usare Modifica e continuazione nelle app C++ di Windows Store e nelle app DirectX perché ora è supportata l'opzione del compilatore `/ZI` con l'opzione  `/bigobj` . È anche possibile usare Modifica e continuazione con file binari compilati con l'opzione `/FASTLINK` .  
  
- Debug in Windows 98.  
  
- Debug in modalità mista (nativo/gestito).  
  
- Debug di JavaScript.  
  
- Debug SQL.  
  
- Debug di un file dump.  
  
- Modifica di codice dopo un'eccezione non gestita, quando l'opzione **Rimuovi stack di chiamate su eccezioni non gestite** non è selezionata.  
  
- Debug di un'app usando **Connetti a** invece di eseguire l'app da **Start** nel menu **Debug** .  
  
- Debug di codice ottimizzato.  
  
- Debug di una versione precedente del codice dopo l'esito negativo della compilazione di una nuova versione a causa di errori di compilazione.  
  
## <a name="BKMK_Linking_limitations"></a> Limitazioni di collegamento  
  
### <a name="BKMK_Linker_options_that_disable_Edit_and_Continue"></a> Opzioni dei linker che disabilitano Modifica e continuazione  
 La funzionalità Modifica e continuazione viene disabilitata dalle seguenti opzioni dei linker:  
  
- L'impostazione di **/OPT:REF**, **/OPT:ICF**o **/INCREMENTAL:NO** provoca la disattivazione di Modifica e continuazione con la visualizzazione del seguente messaggio di avviso:  
  
     LINK : avviso LNK4075: /EDITANDCONTINUE ignorato a causa  
  
     specification  
  
- L'impostazione di **/ORDER**, **/RELEASE**o **/FORCE** provoca la disattivazione di Modifica e continuazione con la visualizzazione del seguente messaggio di avviso:  
  
     LINK : avviso LNK4075: /INCREMENTAL ignorato a causa  
  
     specification  
  
- L'impostazione di qualsiasi opzione che impedisce la creazione di un file di database di programma con estensione pdb provoca la disattivazione di Modifica e continuazione senza la visualizzazione di un messaggio di avviso specifico.  
  
### <a name="BKMK_Auto_relinking_limitations"></a> Limitazioni di ricollegamento automatico  
 Per impostazione predefinita, il programma viene ricollegato automaticamente al termine di una sessione di debug in modalità Modifica e continuazione per creare un eseguibile aggiornato.  
  
 Se il debug viene effettuato da una posizione diversa dal percorso di compilazione originale, non sarà possibile eseguire il ricollegamento automatico. La necessità di eseguire la ricompilazione manualmente viene segnalata con un apposito messaggio.  
  
 Le librerie statiche non vengono ricompilate in modalità Modifica e continuazione. Se si apportano modifiche a una libreria statica con Modifica e continuazione, è necessario ricompilare manualmente la libreria e ricollegare le app che la usano.  
  
 Le istruzioni di compilazione personalizzate non vengono richiamate in modalità Modifica e continuazione. Se il programma usa istruzioni di compilazione personalizzate, sarà possibile effettuare manualmente la ricompilazione affinché tali istruzioni possano essere richiamate. In tal caso, è possibile disabilitare il ricollegamento dopo Modifica e continuazione per fare in modo che venga chiesto se si desidera procedere alla ricompilazione manuale.  
  
 **Per disabilitare il ricollegamento dopo Modifica e continuazione**  
  
1. Scegliere **Opzioni e impostazioni** dal menu **Debug**.  
  
2. Nella finestra di dialogo **Opzioni** nel nodo **Debug** selezionare il nodo **Modifica e continuazione** .  
  
3. Deselezionare la casella di controllo **Ricollega modifiche del codice dopo il debug** .  
  
## <a name="BKMK_Precompiled_Header_Limitations"></a> Limitazioni dei file di intestazione precompilati  
 Per impostazione predefinita, in Modifica e continuazione le intestazioni precompilate vengono caricate ed elaborate in background per velocizzare l'elaborazione delle modifiche al codice. Il caricamento delle intestazioni precompilate richiede l'allocazione di memoria fisica, il che può rappresentare un problema se si effettua la compilazione usando un computer che dispone di una quantità limitata di RAM. È possibile determinare se ciò può costituire un problema usando Gestione attività di Windows per verificare la quantità di memoria fisica disponibile durante il debug. Se la quantità di memoria supera le dimensioni delle intestazioni precompilate, Modifica e continuazione non dovrebbe presentare alcun problema. Se tale quantità è inferiore alle dimensioni delle intestazioni precompilate, è possibile configurare Modifica e continuazione in modo da evitare che le intestazioni precompilate vengano caricate in background.  
  
 **Per disabilitare il caricamento in background delle intestazioni precompilate da parte di Modifica e continuazione**  
  
1. Scegliere **Opzioni e impostazioni** dal menu **Debug**.  
  
2. Nella finestra di dialogo **Opzioni** nel nodo **Debug** selezionare il nodo **Modifica e continuazione** .  
  
3. Deselezionare la casella di controllo **Consenti precompilazione** .  
  
## <a name="BKMK_IDL_Attribute_Limitations"></a> Limitazioni degli attributi IDL  
 Modifica e Continua non consentono di rigenerare file di definizione di interfaccia (IDL). Le modifiche agli attributi IDL non verranno pertanto riflesse mentre si esegue il debug. Per visualizzare il risultato delle modifiche agli attributi IDL è necessario interrompere il debug e ricompilare l'app. Se gli attributi IDL sono stati modificati, non verrà generato alcun errore o avviso. Per altre informazioni, vedere [Attributi IDL](https://msdn.microsoft.com/library/04c596f4-c97b-4952-8053-316678b1d0b6).  
  
## <a name="see-also"></a>Vedere anche  
 [Edit and Continue (Visual C++)](../debugger/edit-and-continue-visual-cpp.md)
