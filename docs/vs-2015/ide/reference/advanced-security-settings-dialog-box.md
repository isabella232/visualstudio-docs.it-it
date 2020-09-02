---
title: Finestra di dialogo Impostazioni di sicurezza avanzate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
- vs.err.debug_in_zone_no_hostproc:11310
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 000c3c4e2996869e96fd0d6097b5bab8576936a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651747"
---
# <a name="advanced-security-settings-dialog-box"></a>Finestra di dialogo Impostazioni di sicurezza avanzate
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Questa finestra di dialogo consente di specificare le impostazioni di sicurezza correlate al debug nell'area di sicurezza.

 Per accedere a questa finestra di dialogo, selezionare un nodo di progetto in **Esplora soluzioni**, quindi scegliere **Proprietà** dal menu **Progetto**. Quando viene visualizzata la **finestra Creazione progetti** , fare clic sulla scheda **sicurezza** . Nella pagina **sicurezza** selezionare **Abilita impostazioni di sicurezza ClickOnce**, fare clic su **un'applicazione con attendibilità parziale**, quindi fare clic su **Avanzate**.

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 **Esegui il debug dell'applicazione con il set di autorizzazioni selezionato** Se si seleziona questa casella di controllo, durante il debug verrà usato il set di autorizzazioni selezionato nella pagina **Sicurezza**. Questa opzione è selezionata per impostazione predefinita.

 Per il corretto funzionamento del debug in un'area di sicurezza è necessario abilitare questa opzione e l'opzione **Abilita processo di hosting di Visual Studio**, disponibile nella pagina **Debug** di **Creazione progetti**.

 Per i progetti Applicazione Web browser WPF, l'opzione **Esegui debug dell'applicazione con il set di autorizzazioni selezionato** è selezionata e disabilitata.

 **Concedi all'applicazione accesso al proprio sito di origine** Se si seleziona questa casella di controllo, l'applicazione può accedere al sito Web o alla condivisione di server in cui è stato pubblicato. Questa opzione è selezionata per impostazione predefinita.

 **Esegui il debug dell'applicazione come se fosse stata scaricata dal seguente URL** Se è necessario consentire all'applicazione di accedere al sito Web o alla condivisione server corrispondente all'**URL di installazione** specificato nella pagina **Pubblica**, digitare qui l'URL. Questa opzione è disponibile solo se la casella di controllo **Concedi all'applicazione accesso al proprio sito di origine** è selezionata.

## <a name="see-also"></a>Vedere anche
 [Pagina Sicurezza, Progettazione progetti](../../ide/reference/security-page-project-designer.md)
