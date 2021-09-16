---
title: Aggiornare l'indirizzo di posta elettronica di accesso del sottoscrittore
description: L'amministratore con privilegi di amministratore con privilegi più grandi vuole aggiornare in blocco il dominio dei sottoscrittori.
ms.topic: include
ms.assetid: c1220a33-26b0-4bf9-be97-ab2b3055e351
author: CaityBuschlen
ms.author: cabuschl
ms.date: 06/01/2021
user.type: admin
tags: ''
subscription.type: vl, cloud, retail, partner
sap.id: b84fffb5-3363-eb7d-224e-1c63faf4067b
ms.openlocfilehash: 56be529658430875502dc388f462e631fd18dc9cda0196f99ee5c27042653797
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "127892569"
---
## <a name="update-subscribers-sign-in-email-address"></a>Aggiornare l'indirizzo di posta elettronica di accesso del sottoscrittore

È possibile aggiornare l'indirizzo di posta elettronica di accesso del sottoscrittore singolarmente o usando la modifica in blocco. 

##  <a name="bulk-edit"></a>Modifiche di massa
1. Nella **pagina Gestisci sottoscrittori** assicurarsi di aver sottoscritto il contratto che deve essere aggiornato.
2. Selezionare **Modifica in** blocco, esportare Excel file e seguire le istruzioni nella finestra popup.
3. Apportare le modifiche necessarie nel file, quindi salvare e caricare il file. Quando si apportano modifiche, tenere presente che i GUID non possono essere modificati.
4. Selezionare **OK** per avviare la modifica in blocco.
5. I sottoscrittori riceveranno un messaggio di posta elettronica che li informa della modifica.

## <a name="individual-edit"></a>Modifica singola 
1. Nella **pagina Gestisci sottoscrittori** assicurarsi di aver sottoscritto il contratto che deve essere aggiornato.
2. Selezionare il sottoscrittore da aggiornare e quindi i puntini di sospensione (...) accanto al nome del sottoscrittore.
3. Selezionare **Edit** (Modifica).
4. Nel pannello a comparsa apportare le modifiche necessarie e quindi selezionare **Salva**.
5. I sottoscrittori riceveranno un messaggio di posta elettronica che li informa della modifica.

## <a name="azure-active-directory-azure-ad"></a>Azure Active Directory (Azure AD) 
Se si assegnano sottoscrizioni usando Azure AD, tutti gli aggiornamenti dell'indirizzo di posta elettronica o del nome vengono visualizzati automaticamente in [manage.visualstudio.com](https://manage.visualstudio.com). Dopo aver salvato le modifiche, gli aggiornamenti verranno visualizzati nel portale di amministrazione entro 24 ore. 
1. Accedere al [portale di Azure](https://portal.azure.com).
2. Apportare gli aggiornamenti necessari.

## <a name="impact-of-sign-in-email-updates"></a>Impatto degli aggiornamenti della posta elettronica di accesso
La modifica del messaggio di posta elettronica di accesso può avere effetti negativi per i sottoscrittori, tra cui:
- Problemi di accesso con l'VISUAL STUDIO IDE.
- Problemi di accesso con Azure DevOps.
- Problemi con il credito individuale mensile di sviluppo/test di Azure.

[Altre informazioni su come la modifica del messaggio di posta elettronica di](https://docs.microsoft.com/visualstudio/subscriptions/subscription-level-changes) accesso può influire sui vantaggi associati del sottoscrittore.
