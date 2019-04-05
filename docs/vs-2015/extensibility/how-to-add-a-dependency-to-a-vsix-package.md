---
title: 'Procedura: Aggiungere una dipendenza a un pacchetto VSIX | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 97118134106614e1e04cd2bc328ad31480618116
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964674"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Procedura: Aggiungere una dipendenza a un pacchetto VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile configurare una distribuzione di pacchetto VSIX che installa le dipendenze che non sono già presenti nel computer di destinazione. A tale scopo, includere le dipendenze VSIX nel file vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Per aggiungere una dipendenza  
  
1.  Aprire il file vsixmanifest nel **progettazione** visualizzazione. Andare alla **dipendenze** scheda e fare clic su **New**.  
  
2.  Per aggiungere un'estensione installata: nel **aggiungere nuove dipendenze** finestra di dialogo **estensione installata** e quindi, per il **nome**, selezionare un'estensione nell'elenco.  
  
3.  Per aggiungere un altro progetto VSIX che non è installato:: nel **aggiungere nuove dipendenze** finestra di dialogo **File nel file system** e quindi usare il **Sfoglia** pulsante per selezionare il progetto VSIX.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti su VSIX Extension Schema 1.0](http://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Preparazione di estensioni per la distribuzione di Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
