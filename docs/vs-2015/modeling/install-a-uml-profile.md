---
title: Installare un profilo UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, profiles
ms.assetid: 586f9ba5-4d01-4a1d-b001-32e2efaa4f24
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 89531fe0f2e912a6aabd962ab56ca7a24a7f3e20
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850657"
---
# <a name="install-a-uml-profile"></a>Installare un profilo UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile estendere Visual Studio con un profilo UML. Un profilo consente di aggiungere stereotipi e altre proprietà agli elementi che è possibile creare nei modelli UML. Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Se si riceve un modello UML creato usando i profili, alcune proprietà non verranno visualizzate a meno che non si installino gli stessi profili.

 Un profilo viene distribuito in un'estensione di Visual Studio. Un'estensione può contenere anche altre funzionalità, ad esempio i comandi di menu. Per ulteriori informazioni, vedere [gestione delle estensioni di Visual Studio](https://msdn.microsoft.com/library/dd293638(VS.100).aspx).

### <a name="to-install-a-uml-profile-on-your-computer"></a>Per installare un profilo UML nel computer

1. Il profilo dovrebbe essere stato fornito sotto forma di file con estensione di Visual Studio (`.vsix`). Nello stesso file potrebbero essere presenti altre funzionalità.

     Spostare il file `.vsix` in una posizione pratica nel file computer.

2. Fare doppio clic sul file `.vsix` in Esplora risorse (o Esplora file) oppure aprirlo in [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

3. Fare clic su **Installa** nella finestra di dialogo visualizzata.

4. Per disinstallare o disabilitare temporaneamente l'estensione, aprire **Gestione estensioni** dal menu **strumenti** .

### <a name="to-uninstall-or-disable-a-profile-extension"></a>Per disinstallare o disabilitare un'estensione profilo

1. Scegliere **Gestione estensioni**dal menu **strumenti** di Visual Studio.

2. Fare clic sull'estensione che si desidera rimuovere e quindi fare clic su **Disabilita** o **Disinstalla**.

## <a name="see-also"></a>Vedere anche
 [Personalizzare il modello con profili e stereotipi](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [definire un profilo per estendere UML](../modeling/define-a-profile-to-extend-uml.md)
