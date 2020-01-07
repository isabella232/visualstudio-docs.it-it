---
title: Finestra di dialogo Impostazioni di sicurezza avanzate
ms.date: 06/27/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 033c8d9c97d54b972a7bf30e9e1e04171e5b505e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595839"
---
# <a name="advanced-security-settings-dialog-box"></a>Finestra di dialogo Impostazioni di protezione avanzate

Questa finestra di dialogo consente di specificare le impostazioni di sicurezza correlate al debug nell'area di sicurezza.

![Finestra di dialogo Impostazioni di sicurezza avanzate in Visual Studio](../media/advanced-security-settings.png)

Per accedere a questa finestra di dialogo, selezionare un nodo di progetto in **Esplora soluzioni**, quindi scegliere **Proprietà** dal menu **Progetto**. Quando viene visualizzata la **finestra Creazione progetti** , fare clic sulla scheda **sicurezza** . Nella pagina **sicurezza** selezionare **Abilita impostazioni di sicurezza ClickOnce**, fare clic su **un'applicazione con attendibilità parziale**, quindi fare clic su **Avanzate**.

## <a name="uielement-list"></a>Elenco UIElement

**Concedi all'applicazione accesso al proprio sito di origine**

Se si seleziona questa casella di controllo, l'applicazione può accedere al sito Web o alla condivisione server in cui è pubblicata. Questa opzione è selezionata per impostazione predefinita.

**Esegui debug dell'applicazione come se fosse stata scaricata dal seguente URL**

Se è necessario consentire all'applicazione di accedere al sito Web o alla condivisione server corrispondente all'**URL di installazione** specificato nella pagina **Pubblica**, immettere qui l'URL. Questa opzione è disponibile solo se la casella di controllo **Concedi all'applicazione accesso al proprio sito di origine** è selezionata.

## <a name="see-also"></a>Vedere anche

- [Pagina Sicurezza, Creazione progetti](../../ide/reference/security-page-project-designer.md)
