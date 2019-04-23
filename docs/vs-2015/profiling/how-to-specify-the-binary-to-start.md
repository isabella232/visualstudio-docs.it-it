---
title: 'Procedura: Specificare il file binario da avviare | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
ms.assetid: ba77fcf4-8d78-49f1-b8f3-7dd0acf84306
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 919e84393cf4aef929a504aadbefe905afe24bfb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60098428"
---
# <a name="how-to-specify-the-binary-to-start"></a>Procedura: Specificare il file binario da avviare
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per profilare file binari, ad esempio le DLL, è necessario immettere informazioni nella finestra di dialogo **Pagine delle proprietà di \<destinazione>**. Queste informazioni indicano dove il progetto DLL può trovare l'applicazione chiamante.  
  
 **Requisiti**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-executable-to-start"></a>Per specificare l'eseguibile da avviare  
  
1. In **Esplora prestazioni** fare clic con il pulsante destro del mouse sul file binario di destinazione e quindi scegliere **Proprietà**.  
  
2. Nella finestra di dialogo **Pagine delle proprietà** fare clic sulle proprietà di **Avvio**.  
  
3. Selezionare la casella di controllo **Eseguire l'override delle impostazioni progetto**.  
  
4. Nella casella di testo **Eseguibile da avviare** specificare il percorso del file.  
  
5. Nella casella di testo **Argomenti** specificare gli argomenti necessari per avviare l'applicazione.  
  
6. Nella casella di testo **Directory di lavoro** specificare il percorso della directory.  
  
7. Fare clic su **OK**.  
  
## <a name="see-also"></a>Vedere anche  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)
