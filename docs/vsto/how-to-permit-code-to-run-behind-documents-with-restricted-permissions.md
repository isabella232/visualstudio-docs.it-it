---
title: Consentire l'esecuzione di codice dietro documenti con autorizzazioni limitate
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
ms.openlocfilehash: 268ca969e9455c33f0ea95c96a83cddabdc026a70fcf42a9f3a1733b6f1ea80a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121243575"
---
# <a name="how-to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Procedura: Consentire l'esecuzione di codice dietro documenti con autorizzazioni limitate
  È possibile usare la funzionalità Information Rights Management (IRM) di Microsoft Office per limitare le autorizzazioni a un documento o a una cartella di lavoro. Per impostazione predefinita, non è consentita l'esecuzione del code-behind Microsoft Office documento di Word o Microsoft Office Excel cartella di lavoro. È possibile modificare l'impostazione predefinita in modo che le estensioni di codice gestito possano accedere al modello a oggetti e la soluzione funzioni.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Per poter modificare le impostazioni delle autorizzazioni, è necessario essere l'autore del documento o della cartella di lavoro o disporre dell'accesso Controllo completo.

## <a name="to-permit-code-to-run-behind-documents-with-restricted-permissions"></a>Per consentire l'esecuzione di codice dietro documenti con autorizzazioni limitate

1. Aprire il documento o la cartella di lavoro in Word o Excel.

2. Fare clic **sulla scheda File** , scegliere **Prepara**, limita **autorizzazione** e quindi fare clic su Accesso **con restrizioni**.

   > [!NOTE]
   > Al primo utilizzo, viene richiesto di installare il client Windows Rights Management client. Dopo aver installato il client, potrebbe essere necessario ripetere i passaggi.

3. Nella finestra **di dialogo** Autorizzazione selezionare **Limita l'autorizzazione per questo documento** e quindi fare clic su Altre **opzioni**.

4. In **Autorizzazioni aggiuntive per gli utenti** selezionare Accedi al contenuto a livello di **codice.**

   Word o Excel consentirà l'accesso a livello di codice al modello a oggetti.

## <a name="see-also"></a>Vedi anche
- [Panoramica di Information Rights Management e delle estensioni di codice gestito](../vsto/information-rights-management-and-managed-code-extensions-overview.md)
- [Protezione dei documenti nelle soluzioni a livello di documento](../vsto/document-protection-in-document-level-solutions.md)
- [Protezione con password Office documenti](../vsto/password-protection-on-office-documents.md)
- [Progettare e creare Office soluzioni](../vsto/designing-and-creating-office-solutions.md)
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
- [Distribuire una soluzione Office distribuzione](../vsto/deploying-an-office-solution.md)
