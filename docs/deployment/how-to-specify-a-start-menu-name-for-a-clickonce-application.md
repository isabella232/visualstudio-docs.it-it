---
title: "Procedura: specificare il nome di un menu Start per un'applicazione ClickOnce | Microsoft Docs"
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 882d6f7471530a101404040368dbc6088e9b5d96
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381925"
---
# <a name="how-to-specify-a-start-menu-name-for-a-clickonce-application"></a>Procedura: Specificare il nome di un'applicazione ClickOnce per il menu Start
Quando un' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione viene installata per l'utilizzo online e offline, viene aggiunta una voce al menu **Start** e all'elenco **Installazione applicazioni** . Per impostazione predefinita, il nome visualizzato corrisponde al nome dell'assembly dell'applicazione, ma è possibile modificare il nome visualizzato impostando **nome prodotto** nella finestra di dialogo **Opzioni di pubblicazione** .

 Il **nome del prodotto** verrà visualizzato nella pagina *publish.htm* ; per un'applicazione offline installata, sarà il nome della voce nel menu **Start** , che sarà anche il nome che viene visualizzato in **installazione**applicazioni.

 **Il nome del server di pubblicazione** verrà visualizzato nella pagina *publish.htm* sopra il **nome del prodotto**e, per un'applicazione offline installata, sarà anche il nome della cartella che contiene l'icona dell'applicazione nel menu **Start** .

 Il collegamento al menu Start o il riferimento all'app viene creato in *%AppData%\Microsoft\Windows\Start avvio\programmi \\<nome \> dell'autore*. Il collegamento o il riferimento all'app ha lo stesso nome del nome del prodotto.

 È possibile impostare le proprietà **nome prodotto** e **nome server di pubblicazione** nella finestra di dialogo **Opzioni di pubblicazione** , disponibile nella pagina **pubblica** di **Progettazione progetti**.

### <a name="to-specify-a-start-menu-name"></a>Per specificare il nome di un menu Start

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic sul pulsante **Opzioni** per aprire la finestra di dialogo **Opzioni di pubblicazione** .

4. Fare clic su **Descrizione**.

5. Nella finestra di dialogo **Opzioni di pubblicazione** immettere il nome da visualizzare in **Product Name**.

6. Facoltativamente, è possibile immettere un nome del server di pubblicazione nel **nome dell'editore**.

## <a name="see-also"></a>Vedi anche
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)