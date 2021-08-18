---
title: Specificare menu Start nome per un'app ClickOnce predefinita
description: Informazioni su come modificare il nome visualizzato per l'applicazione ClickOnce impostando Nome prodotto nella finestra di dialogo Opzioni di pubblicazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Start menu resource name
- Start menu name
- ClickOnce deployment, Start menu name
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 18e91e0bb0ebcb6a88d6f4c197cce9dfb4a04592
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051586"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Procedura: Specificare il nome di un'applicazione ClickOnce per il menu Start
Quando un'applicazione viene installata sia per l'uso online che offline, viene aggiunta una voce al menu Start e [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] all'elenco **Installazione** applicazioni.  Per impostazione predefinita, il nome visualizzato corrisponde al nome dell'assembly dell'applicazione, ma è possibile modificare il nome visualizzato impostando **Nome prodotto** nella finestra di dialogo **Opzioni** di pubblicazione .

 **Il nome** del prodotto verrà visualizzato nella *publish.htm.* per un'applicazione offline installata, sarà il nome della voce nel menu **Start** e sarà anche il nome visualizzato in Installazione **applicazioni**.

 **Publisher** nome verrà visualizzato nella pagina *publish.htm* sopra Nome prodotto e, per un'applicazione offline installata, sarà anche il nome della cartella che contiene l'icona dell'applicazione nel menu **Start.**

 Il menu Start collegamento o il riferimento all'app viene creato in *%appdata%\Microsoft\Windows\Menu Start\Programmi<\\ publisher. \>* Il collegamento o il riferimento all'app ha lo stesso nome del nome del prodotto.

 È possibile impostare le **proprietà Product name** **e Publisher name** nella finestra  di dialogo **Opzioni** di pubblicazione, disponibile nella pagina Pubblica di **Project Designer**.

### <a name="to-specify-a-start-menu-name"></a>Per specificare un nome menu Start

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic **sul pulsante** Opzioni per aprire la finestra di **dialogo Opzioni** di pubblicazione .

4. Fare clic **su Descrizione**.

5. Nella finestra **di dialogo Opzioni** di pubblicazione immettere il nome da visualizzare in Nome **prodotto**.

6. Facoltativamente, è possibile immettere un nome di editore Publisher **nome**.

## <a name="see-also"></a>Vedi anche
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: Pubblicare un'ClickOnce usando la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)