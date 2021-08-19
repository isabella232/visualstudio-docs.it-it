---
title: Consentire l'esecuzione del codice dietro la documentazione con autorizzazioni limitate
description: Informazioni su come consentire l'esecuzione di codice dietro documenti con autorizzazioni limitate usando Office di sviluppo in Visual Studio.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 366c8716995f0f5e88707d738957fc4ec0476a50
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083388"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Procedura: Consentire l'esecuzione di codice dietro documenti con autorizzazioni limitate
  È possibile usare la funzionalità Information Rights Management (IRM) di Microsoft Office limitare le autorizzazioni per un documento o una cartella di lavoro. Per impostazione predefinita, non è consentita l'esecuzione del code-behind Microsoft Office un documento di Word o di Microsoft Office Excel cartella di lavoro. È possibile modificare l'impostazione predefinita in modo che le estensioni di codice gestito possano accedere al modello a oggetti e la soluzione funzioni.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 È necessario essere l'autore del documento o della cartella di lavoro o disporre dell'accesso Controllo completo per poter modificare le impostazioni delle autorizzazioni.

## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Per consentire l'esecuzione di codice dietro documenti con autorizzazioni limitate

1. Aprire il documento o la cartella di lavoro in Word o Excel.

2. Fare clic **sulla scheda File** , scegliere **Prepara**, Limita **autorizzazionee** quindi fare clic su **Accesso limitato**.

   > [!NOTE]
   > Al primo utilizzo, viene richiesto di installare il client Windows Rights Management client. Dopo aver installato il client, potrebbe essere necessario ripetere i passaggi.

3. Nella finestra **di dialogo** Autorizzazione selezionare Limita autorizzazione a **questo documento** e quindi fare clic su **Altre opzioni.**

4. In **Autorizzazioni aggiuntive per gli utenti selezionare** Accedi al contenuto a livello di **codice.**

   Word o Excel consente l'accesso a livello di codice al modello a oggetti.

## <a name="see-also"></a>Vedi anche
- [Panoramica di Information Rights Management e delle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Protezione dei documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)
- [Protezione della password nei Office dati](../vsto/password-protection-on-office-documents.md)
- [Progettare e creare Office soluzioni](../vsto/designing-and-creating-office-solutions.md)
- [Proteggere Office soluzioni](../vsto/securing-office-solutions.md)
- [Distribuire una Office distribuzione](../vsto/deploying-an-office-solution.md)
