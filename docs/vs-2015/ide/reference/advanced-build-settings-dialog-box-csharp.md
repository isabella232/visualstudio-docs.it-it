---
title: Finestra di dialogo Impostazioni di compilazione avanzate (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 38f4d233c8804bec91d2f7dfd2dc34c6879e8be9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651731"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Finestra di dialogo Impostazioni di compilazione avanzate (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Per specificare le proprietà di configurazione di compilazione avanzate del progetto, usare la finestra di dialogo **Impostazioni di compilazione avanzate** di **Creazione progetti**. Questa finestra di dialogo è applicabile solo ai progetti [!INCLUDE[csprcs](../../includes/csprcs-md.md)].

## <a name="general"></a>Generale
 Le opzioni seguenti consentono di configurare le impostazioni avanzate generali.

 **Versione linguaggio** Specifica la versione del linguaggio da usare. Il set di funzionalità varia a seconda della versione. Questa opzione può quindi essere usata per forzare il compilatore ad attivare solo un sottoinsieme delle funzionalità implementate oppure solo le funzionalità compatibili con uno standard esistente. Le opzioni di questa impostazione sono le seguenti:

- **ISO-1**

   Fa riferimento alle funzionalità standard ISO-1.

- **default**

   Fa riferimento alla versione corrente.

  Per altre informazioni, vedere [/langversion (Opzioni del compilatore C#)](https://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).

  **Segnalazione errori interni del compilatore** Specifica se gli errori del compilatore devono essere segnalati a Microsoft. Se l'opzione è impostata su **prompt**, al verificarsi di un errore del compilatore interno sarà chiesto se si vuole inviare elettronicamente a Microsoft una segnalazione errori. Se è impostata su **send**, sarà inviata automaticamente una segnalazione errori. Se è impostata su **queue**, le segnalazioni errori saranno accodate. Se è impostata su **none**, l'errore sarà segnalato soltanto nell'output di testo del compilatore. Per altre informazioni, vedere [/errorreport (Opzioni del compilatore C#)](https://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).

  **Verifica overflow/underflow aritmetico** Specifica se un'istruzione aritmetica Integer non inclusa nell'ambito delle parole chiave [checked](https://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) o [unchecked](https://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) e che restituisce un valore non compreso nell'intervallo del tipo di dati provocherà un'eccezione in fase di esecuzione. Per ulteriori informazioni, vedere [/Checked (C# opzioni del compilatore)](https://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).

  **Ometti riferimenti a mscorlib.dll** Specifica se nel programma sarà importato il file mscorlib.dll per l'intero spazio dei nomi <xref:System>. Selezionare questa casella se si vuole definire o creare lo spazio dei nomi <xref:System> e gli oggetti personalizzati. Per altre informazioni, vedere [/nostdlib (Opzioni del compilatore C#)](https://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).

## <a name="output"></a>Output
 Le opzioni seguenti consentono di specificare impostazioni di output avanzate.

 **Informazioni di debug** Specifica il tipo di informazioni di debug generate dal compilatore. Per informazioni su come configurare le prestazioni di debug di un'applicazione, vedere [Semplificazione del debug di un'immagine](https://msdn.microsoft.com/library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3). Le opzioni di questa impostazione sono le seguenti:

- **none**

   Specifica che non saranno generate informazioni di debug

- **full**

   Consente di associare un debugger al programma in esecuzione.

- **pdbonly**

   Consente il debug del codice sorgente quando il programma viene avviato nel debugger, ma l'assembler viene visualizzato solo se il programma in esecuzione è associato al debugger.

  Per altre informazioni, vedere [/debug (Opzioni del compilatore C#)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).

  **Allineamento file** Specifica le dimensioni delle sezioni nel file di output. I valori validi sono **512**, **1024**, **2048**, **4096** e **8192**. Questi valori sono misurati in byte. Ogni sezione sarà allineata in base a un limite multiplo di questo valore, determinando così le dimensioni del file di output. Per altre informazioni, vedere [/filealign (Opzioni del compilatore C#)](https://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).

  **Indirizzo di base dll** Specifica l'indirizzo di base preferito in cui caricare una DLL. L'indirizzo di base predefinito per una DLL viene impostato dal Common Language Runtime [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Per altre informazioni, vedere [/baseaddress (Opzioni del compilatore C#)](https://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).

## <a name="see-also"></a>Vedere anche
 [Opzioni del compilatore C#](https://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44) [Pagina Compilazione, Progettazione progetti (C#)](../../ide/reference/build-page-project-designer-csharp.md)
