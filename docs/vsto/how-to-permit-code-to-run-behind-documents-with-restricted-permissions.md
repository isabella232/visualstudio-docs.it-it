---
title: Consentire l'esecuzione del codice dietro i documenti con autorizzazioni limitate
description: Informazioni su come consentire l'esecuzione di codice dietro i documenti con autorizzazioni limitate usando gli strumenti di sviluppo per Office in Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Information Rights Management [Office development in Visual Studio]
- permissions [Office development in Visual Studio]
- IRM [Office development in Visual Studio]
- code [Office development in Visual Studio], running behind restricted documents
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1a65e99712658567996598d2190447ff09cf9b05
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888888"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Procedura: consentire l'esecuzione del codice dietro i documenti con autorizzazioni limitate
  È possibile utilizzare la funzionalità Information Rights Management (IRM) di Microsoft Office per limitare le autorizzazioni a un documento o a una cartella di lavoro. Per impostazione predefinita, non è consentita l'esecuzione del codice sottostante a un documento Microsoft Office Word con restrizioni o Microsoft Office cartella di lavoro di Excel. È possibile modificare l'impostazione predefinita in modo che le estensioni del codice gestito possano accedere al modello a oggetti e la soluzione funzionerà.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Per modificare le impostazioni delle autorizzazioni, è necessario essere l'autore del documento o della cartella di lavoro oppure disporre di un accesso controllo completo.

## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Per consentire l'esecuzione del codice dietro i documenti con autorizzazioni limitate

1. Aprire il documento o la cartella di lavoro in Word o Excel.

2. Fare clic sulla scheda **file** , scegliere **prepara**, scegliere **limita autorizzazione** e quindi fare clic su **accesso limitato**.

   > [!NOTE]
   > Al primo utilizzo, viene richiesto di installare il client Windows Rights Management. Dopo aver installato il client, potrebbe essere necessario ripetere i passaggi.

3. Nella finestra di dialogo **autorizzazione** selezionare **limita autorizzazione al documento** e quindi fare clic su **altre opzioni**.

4. In **autorizzazioni aggiuntive per gli utenti** selezionare **accedi al contenuto a livello di codice**.

   Word o Excel consentirà l'accesso programmatico al modello a oggetti.

## <a name="see-also"></a>Vedi anche
- [Panoramica di Information Rights Management e delle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Protezione di documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)
- [Protezione delle password nei documenti di Office](../vsto/password-protection-on-office-documents.md)
- [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
