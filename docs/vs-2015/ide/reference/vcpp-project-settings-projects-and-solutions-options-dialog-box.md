---
title: Impostazioni progetto di VC++, Progetti e soluzioni, finestra di dialogo Opzioni | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Projects.VCBuild
helpviewer_keywords:
- builds [Visual Studio], logs
- build process [C++]
- files [Visual Studio], built by C/C++ compiler
- file extensions, built by C or C++ compiler
- cl.exe compiler, file extensions
- extensions, files built by C or C++ compiler
- BuildLog.htm
ms.assetid: 56420efd-6a95-464e-b890-e2b38c48d66a
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8b6f588a1361c9184b67e510688128f621754f82
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517607"
---
# <a name="vc-project-settings-projects-and-solutions-options-dialog-box"></a>Impostazioni progetto di VC++, Progetti e soluzioni, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [impostazioni di progetto VC + +, progetti e soluzioni, finestra di dialogo Opzioni](https://docs.microsoft.com/visualstudio/ide/reference/vcpp-project-settings-projects-and-solutions-options-dialog-box).  
  
  
Questa finestra di dialogo consente di definire le impostazioni del progetto [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] relative ai log di compilazione e ai tipi di file supportati.  
  
### <a name="to-access-this-dialog-box"></a>Per accedere a questa finestra di dialogo  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Selezionare **Progetti e soluzioni** e quindi **Impostazioni progetto di VC++**.  
  
## <a name="build-customization-search-path"></a>Percorso di ricerca per le personalizzazioni delle compilazioni  
 Specifica l'elenco delle directory che contengono i file con estensione rule, che consentono di definire le regole di compilazione per i progetti.  
  
## <a name="build-logging"></a>Log di compilazione  
 **Sì**  
 Attiva la generazione del file di log di compilazione. Con questa opzione viene generato il file BuildLog.htm, reperibile nella directory dei file intermedi del progetto. Tale file viene sovrascritto a ogni nuova ricompilazione.  
  
 **No**  
 Disattiva la generazione del file di log di compilazione.  
  
## <a name="build-timing"></a>Durata compilazione  
 **Sì**  
 Attiva la registrazione della durata della compilazione. Se questa opzione è selezionata, il tempo necessario per il completamento della compilazione viene inviato alla finestra di output. Per altre informazioni, vedere [Finestra di output](../../ide/reference/output-window.md).  
  
 **No**  
 Disattiva la registrazione della durata della compilazione.  
  
## <a name="extensions-to-hide"></a>Estensioni da nascondere  
 Specifica le estensioni di file che non verranno visualizzate in **Esplora soluzioni** quando l'opzione **Mostra tutti i file** è abilitata.  
  
## <a name="extensions-to-include"></a>Estensioni da includere  
 Specifica le estensioni di file che è possibile trasferire nel progetto.  
  
## <a name="maximum-concurrent-c-compilations"></a>Numero massimo di compilazioni C++ simultanee  
 Specifica il numero massimo di core CPU da usare per la compilazione C++ in parallelo.  
  
## <a name="show-environment-in-log"></a>Mostra ambiente nel log  
 **Sì**  
 Elenca le variabili di ambiente presenti nel file di log di compilazione. Questa opzione specifica se attivare o meno nel file di log di compilazione l'eco di tutte le variabili di ambiente durante la compilazione di progetti [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].  
  
 **No**  
 Esclude le variabili di ambiente dal file di log di compilazione.  
  
## <a name="solution-explorer-mode"></a>Modalità Esplora soluzioni  
 **Mostra solo i file del progetto**  
 Configura **Esplora soluzioni** in modo da visualizzare solo i file del progetto.  
  
 **Mostra tutti i file**  
 Configura **Esplora soluzioni** in modo da visualizzare i file del progetto e quelli presenti su disco nella cartella del progetto.  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione di programmi C/C++](http://msdn.microsoft.com/library/fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008)   
 [Riferimenti alla compilazione in C/C++](http://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d)



