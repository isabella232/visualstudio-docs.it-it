---
title: 'Procedura: aggiungere una dipendenza a un pacchetto VSIX | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4a8f360470b22722a3008ed1ac1c05a411cd47d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800360"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Procedura: aggiungere una dipendenza a un pacchetto VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile configurare una distribuzione di pacchetto VSIX che installa le dipendenze che non sono già presenti nel computer di destinazione. A tale scopo, includere le dipendenze VSIX nel file vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Per aggiungere una dipendenza  
  
1.  Aprire il file vsixmanifest nel **progettazione** visualizzazione. Andare alla **dipendenze** scheda e fare clic su **New**.  
  
2.  Per aggiungere un'estensione installata: nel **aggiungere nuove dipendenze** finestra di dialogo **estensione installata** e quindi, per il **nome**, selezionare un'estensione nell'elenco.  
  
3.  Per aggiungere un altro progetto VSIX che non è installato:: nel **aggiungere nuove dipendenze** finestra di dialogo **File nel file system** e quindi usare il **Sfoglia** pulsante per selezionare il progetto VSIX.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti su VSIX Extension Schema 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Preparazione di estensioni per la distribuzione di Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)

