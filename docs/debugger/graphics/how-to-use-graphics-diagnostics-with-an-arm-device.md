---
title: 'Procedura: usare la diagnostica grafica con un dispositivo ARM | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: eedc7e454c6523c1ab29e4ae685b14954c8e6d98
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-graphics-diagnostics-with-an-arm-device"></a>Procedura: Usare la diagnostica della grafica con un dispositivo ARM
La diagnostica della grafica supporta il debug remoto di app Direct3D su dispositivi basati su ARM che eseguono Windows RT 8.1 o Windows Phone 8.1. È possibile acquisire informazioni grafiche dall'app Direct3D mentre è in esecuzione nel dispositivo oppure usare quest'ultimo come dispositivo di riproduzione per le informazioni grafiche acquisite in precedenza.  
  
## <a name="using-graphics-diagnostics-with-an-arm-based-device"></a>Uso della diagnostica grafica con un dispositivo basato su ARM  
 Dato che Visual Studio non può essere eseguito su dispositivi basati su ARM, è necessario usare il debugger remoto per analizzare app che vengono eseguite su tali dispositivi. Il debugger remoto supporta l'acquisizione e la riproduzione della grafica, consentendo in tal modo di diagnosticare errori di rendering e di valutare le prestazioni grafiche su qual tipo di dispositivi con la stessa semplicità con cui vi si esegue il debug dell'app.  
  
 Per usare le funzionalità di diagnostica grafica, abilitare prima il debug remoto nel dispositivo.  
  
#### <a name="to-enable-remote-debugging-on-your-arm-based-device"></a>Per abilitare il debug remoto in un dispositivo basato su ARM  
  
1.  Installare il [criteri dei kit ARM](http://msdn.microsoft.com/windows/desktop/dn469188) nel dispositivo basato su ARM.  
  
2.  Installare il [strumenti di debug remoto](http://go.microsoft.com/fwlink/?LinkId=393086) nel dispositivo basato su ARM.  
  
> [!IMPORTANT]
>  Per dispositivi Windows Phone 8.1, potrebbe essere necessario registrare il proprio telefono per lo sviluppo. Per tale operazione è necessario essere uno sviluppatore registrato. Per ulteriori informazioni, vedere [come distribuire ed eseguire un'app per Windows Phone 8](http://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx).  
  
 Dopo aver abilitato il debug remoto nel dispositivo, renderlo la destinazione del debug e avviare la diagnostica della grafica.  
  
#### <a name="to-configure-and-start-graphics-diagnostics-on-your-device"></a>Per configurare e avviare la diagnostica della grafica nel dispositivo  
  
1.  Nel **piattaforme soluzione** elenco a discesa, seleziona **ARM** in modo che il dispositivo basato su ARM sarà disponibile come destinazione di debug remota.  
  
2.  Nel **destinazione di Debug** elenco a discesa selezionare il dispositivo ARM.  
  
3.  Scegliere il menu **Debug**, **grafica**, **avvia diagnostica**. (da tastiera: ALT+F5)  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire App UWP in un computer remoto](../run-windows-store-apps-on-a-remote-machine.md)   
 [Procedura: Modificare il computer di riproduzione della diagnostica della grafica](how-to-change-the-graphics-diagnostics-playback-machine.md)