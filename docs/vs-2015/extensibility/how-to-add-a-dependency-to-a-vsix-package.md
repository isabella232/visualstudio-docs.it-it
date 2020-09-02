---
title: 'Procedura: aggiungere una dipendenza a un pacchetto VSIX | Microsoft Docs'
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
ms.openlocfilehash: 997c0df133b72d69dfb4e69de53a1b77e1a0965c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697500"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Procedura: Aggiungere una dipendenza a un pacchetto VSIX
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile configurare una distribuzione di pacchetti VSIX che consente di installare tutte le dipendenze che non sono già presenti nel computer di destinazione. A tale scopo, includere le dipendenze VSIX nel file source. Extension. vsixmanifest.  
  
#### <a name="to-add-a-dependency"></a>Per aggiungere una dipendenza  
  
1. Aprire il file source. Extension. vsixmanifest nella visualizzazione **progettazione** . Passare alla scheda **dipendenze** e fare clic su **nuovo**.  
  
2. Per aggiungere un'estensione installata: nella finestra di dialogo **Aggiungi nuova dipendenza** selezionare **estensione installata** , quindi selezionare un'estensione nell'elenco come **nome**.  
  
3. Per aggiungere un altro progetto VSIX non installato:: nella finestra di dialogo **Aggiungi nuova dipendenza** selezionare **file in file System** e quindi usare il pulsante **Sfoglia** per selezionare il progetto VSIX.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo schema di estensione VSIX 1,0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Preparazione di estensioni per la distribuzione di Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
