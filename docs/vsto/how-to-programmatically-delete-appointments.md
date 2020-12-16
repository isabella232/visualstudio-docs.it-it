---
title: 'Procedura: eliminare appuntamenti a livello di codice'
description: Informazioni su come è possibile eliminare nomine in Microsoft Outlook a livello di codice. Questo esempio elimina un'istanza di un appuntamento ricorrente.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- calendars [Office development in Visual Studio], deleting appointments
- deleting appointments
- appointments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 56bd9876fa24610412d66e71800a24b413dac576
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526807"
---
# <a name="how-to-programmatically-delete-appointments"></a>Procedura: eliminare appuntamenti a livello di codice
  Questo esempio elimina un'istanza di un appuntamento ricorrente. L'esempio presuppone che un'istanza di un appuntamento ricorrente si verifica il 28 giugno 2006 alle 08.00.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 [!code-vb[Trin_Outlook_RL_DeleteAppointment#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_DeleteAppointment/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_DeleteAppointment#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_DeleteAppointment/thisaddin.cs#1)]

## <a name="see-also"></a>Vedere anche
- [Usare gli elementi del calendario](../vsto/working-with-calendar-items.md)
- [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Procedura: creare appuntamenti a livello di codice](../vsto/how-to-programmatically-create-appointments.md)
- [Procedura: creare un calendario personalizzato a livello di codice](../vsto/how-to-programmatically-create-a-custom-calendar.md)
- [Procedura: creare una richiesta di riunione a livello di codice](../vsto/how-to-programmatically-create-a-meeting-request.md)
