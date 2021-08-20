---
title: Incrementare automaticamente la versione ClickOnce pubblicazione
description: Informazioni su come disabilitare l'incremento automatico del numero di revisione per l ClickOnce appliazione usando Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: c2f4db86a97743d8844ef7664d31cdf3649a14c7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127987"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Procedura: Incrementare automaticamente il numero di versione della pubblicazione dell'applicazione ClickOnce

Quando si pubblica [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] un'applicazione, la modifica della proprietà determina `Publish Version` la pubblicazione dell'applicazione come aggiornamento. Per impostazione predefinita, Visual Studio incrementa automaticamente il `Revision` numero di ogni volta che si pubblica `Publish Version` l'applicazione.

È possibile disabilitare questo comportamento nella **pagina Pubblica** di progettazione **Project .**

> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>Per disabilitare l'incremento automatico della versione di pubblicazione

1. Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.

2. Fare clic sulla scheda **Pubblica**.

3. Nella sezione **Versione pubblicazione** deselezionare la casella di **controllo Incrementa automaticamente revisione** a ogni versione.

## <a name="see-also"></a>Vedi anche

- [Procedura: Impostare la versione pubblicazione per un'applicazione ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: Pubblicare un'ClickOnce di pubblicazione usando la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)