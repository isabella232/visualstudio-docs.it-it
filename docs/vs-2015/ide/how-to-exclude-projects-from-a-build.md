---
title: 'Procedura: Escludere progetti da una compilazione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6a0b46a4aaa780357faa38a9ee4b01d04b1a0ba1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178856"
---
# <a name="how-to-exclude-projects-from-a-build"></a>Procedura: Escludere progetti da una compilazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile compilare una soluzione senza compilare tutti i progetti contenuti al suo interno. Ad esempio, si può escludere un progetto che causa l'interruzione della compilazione. Sarà possibile compilare il progetto in seguito, dopo avere esaminato e risolto i problemi.  
  
 Per escludere un progetto è possibile procedere in due modi:  
  
- Rimuoverlo temporaneamente dalla configurazione della soluzione attiva.  
  
- Creare di una configurazione di soluzione che non include il progetto.  
  
  Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).  
  
### <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Per rimuovere temporaneamente un progetto dalla configurazione della soluzione attiva.  
  
1. Nella barra dei menu scegliere **Compilazione**, **Gestione configurazione**.  
  
2. Nella tabella **Contesti progetto** individuare il progetto da escludere dalla compilazione.  
  
3. Nella colonna **Compilazione** del progetto deselezionare la casella di controllo.  
  
4. Scegliere il pulsante **Chiudi** e quindi ricompilare la soluzione.  
  
### <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Per creare una configurazione di soluzione che esclude un progetto  
  
1. Nella barra dei menu scegliere **Compilazione**, **Gestione configurazione**.  
  
2. Nell'elenco **Configurazione soluzione attiva** **scegliere \<Nuova**.  
  
3. Nella casella **Nome** immettere un nome per la configurazione della soluzione.  
  
4. Nell'elenco **Copia impostazioni da** scegliere la configurazione di soluzione su cui si vuole basare la nuova configurazione (ad esempio **Debug**) e quindi scegliere il pulsante **OK**.  
  
5. Nella finestra di dialogo **Configuration Manager** deselezionare la casella di controllo **Compilazione** per il progetto da escludere e quindi scegliere il pulsante **Chiudi**.  
  
6. Sulla barra degli strumenti **Standard** verificare che la nuova configurazione della soluzione compaia come configurazione attiva nella casella **Configurazioni soluzione**.  
  
7. Sulla barra dei menu scegliere **Compila**, **Ricompila soluzione**.  
  
## <a name="see-also"></a>Vedere anche  
 [Understanding Build Configurations](../ide/understanding-build-configurations.md)  (Informazioni sulle configurazioni delle compilazioni)  
 [Procedura: Creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md)   
 [Procedura: Compilare più configurazioni contemporaneamente](../ide/how-to-build-multiple-configurations-simultaneously.md)
