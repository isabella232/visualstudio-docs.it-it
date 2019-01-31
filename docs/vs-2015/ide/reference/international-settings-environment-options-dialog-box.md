---
title: Impostazioni internazionali, Ambiente, finestra di dialogo Opzioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
- VS.ToolsOptionsPag.Environment.International_Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: fcfc0d02b8ffd0d1e178bdde363736d14d99fa17
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54754944"
---
# <a name="international-settings-environment-options-dialog-box"></a>Impostazioni internazionali, Ambiente, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
La pagina Impostazioni internazionali consente di modificare la lingua predefinita quando ci sono più versioni in lingue diverse dell'IDE (Integrated Development Environment) installato sul proprio computer. È possibile accedere a questa finestra di dialogo selezionando **Opzioni** dal menu **Strumenti** e scegliendo **Impostazioni internazionali** dalla cartella **Ambiente**. Se questa pagina non viene visualizzata nell'elenco, selezionare **Mostra tutte le impostazioni** nella finestra di dialogo **Opzioni**.  
  
> [!NOTE]
>  Le opzioni disponibili nelle finestre di dialogo e i nomi e i percorsi dei comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida a seconda dell'edizione o delle impostazioni attive. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 **Lingua**  
 Elenca le lingue disponibili per le versioni di lingua del prodotto installato. Questa opzione non è disponibile a meno che non vi siano più versioni di lingua installate sul proprio computer. Se l'ambiente è condiviso da più lingue di prodotti o da un'installazione mista di lingue dei prodotti, la selezione della lingua viene modificata in **Come Microsoft Windows**.  
  
> [!CAUTION]
>  In un sistema con più lingue installate, gli strumenti di compilazione Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe e file correlati) non sono interessati da questa impostazione. Questi strumenti usano la versione dell'ultima lingua installata, sovrascrivendo quelli per la lingua precedentemente installata perché gli strumenti di compilazione di Visual C++ non usano il modello DLL satellite.  
  
## <a name="see-also"></a>Vedere anche  
 [Finestra di dialogo Opzioni ambiente](../../ide/reference/environment-options-dialog-box.md)
