---
title: Finestra di dialogo Impostazioni di sicurezza avanzate
description: La finestra Impostazioni sicurezza avanzata consente di specificare le impostazioni di sicurezza correlate al debug nell'area .
ms.custom: SEO-VS-2020
ms.date: 06/27/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- vs.err.debug_in_zone_no_hostproc
helpviewer_keywords:
- Advanced Security Settings dialog box
ms.assetid: 2e7aefe9-6d20-4f3e-b257-aee1ebcc6f5d
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c5831e95f907fce068868fa8c2da91c2ada6fbb65cb90e4603c4cc2fecf70d34
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121259045"
---
# <a name="advanced-security-settings-dialog-box"></a>Finestra di dialogo Impostazioni di sicurezza avanzate

Questa finestra di dialogo consente di specificare le impostazioni di sicurezza correlate al debug nell'area di sicurezza.

![Finestra di dialogo Impostazioni di sicurezza avanzate in Visual Studio](../media/advanced-security-settings.png)

Per accedere a questa finestra di dialogo, selezionare un nodo di progetto in **Esplora soluzioni**, quindi scegliere **Proprietà** dal menu **Progetto**. Quando viene **visualizzata Project,** fare clic sulla **scheda** Sicurezza . Nella pagina **Sicurezza** selezionare Abilita ClickOnce **sicurezza Impostazioni**, fare clic su Questa è un'applicazione parzialmente attendibile **e** quindi fare clic su **Avanzate.**

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia

**Concedi all'applicazione accesso al proprio sito di origine**

Se si seleziona questa casella di controllo, l'applicazione può accedere al sito Web o alla condivisione server in cui è pubblicata. Questa opzione è selezionata per impostazione predefinita.

**Esegui debug dell'applicazione come se fosse stata scaricata dal seguente URL**

Se è necessario consentire all'applicazione di accedere al sito Web o alla condivisione server corrispondente all'**URL di installazione** specificato nella pagina **Pubblica**, immettere qui l'URL. Questa opzione è disponibile solo se la casella di controllo **Concedi all'applicazione accesso al proprio sito di origine** è selezionata.

## <a name="see-also"></a>Vedi anche

- [Pagina Sicurezza, Progettazione progetti](../../ide/reference/security-page-project-designer.md)
