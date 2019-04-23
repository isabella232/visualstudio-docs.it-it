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
ms.openlocfilehash: cbd9426b7a9190872a2b04246d7f051b480a188d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066884"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Procedura: Aggiungere una dipendenza a un pacchetto VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile configurare una distribuzione di pacchetto VSIX che installa le dipendenze che non sono già presenti nel computer di destinazione. A tale scopo, includere le dipendenze VSIX nel file vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Per aggiungere una dipendenza  
  
1. Aprire il file vsixmanifest nel **progettazione** visualizzazione. Andare alla **dipendenze** scheda e fare clic su **New**.  
  
2. Per aggiungere un'estensione installata: nel **aggiungere nuove dipendenze** finestra di dialogo **estensione installata** e quindi, per il **nome**, selezionare un'estensione nell'elenco.  
  
3. Per aggiungere un altro progetto VSIX che non è installato:: nel **aggiungere nuove dipendenze** finestra di dialogo **File nel file system** e quindi usare il **Sfoglia** pulsante per selezionare il progetto VSIX.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti su VSIX Extension Schema 1.0](http://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Preparazione di estensioni per la distribuzione di Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
