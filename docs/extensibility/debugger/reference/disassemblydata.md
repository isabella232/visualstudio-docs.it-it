---
description: Descrive un'istruzione disassembly per l'ambiente di sviluppo integrato (IDE) da visualizzare.
title: DisassemblyData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e76a231891235f26ea4b4cd675f341376de4ff97ef7e6b2540a1cd1318504ce6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121262555"
---
# <a name="disassemblydata"></a>DisassemblyData
Descrive un'istruzione disassembly per l'ambiente di sviluppo integrato (IDE) da visualizzare.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct tagDisassemblyData {
    DISASSEMBLY_STREAM_FIELDS dwFields;
    BSTR                      bstrAddress;
    BSTR                      bstrAddressOffset;
    BSTR                      bstrCodeBytes;
    BSTR                      bstrOpcode;
    BSTR                      bstrOperands;
    BSTR                      bstrSymbol;
    UINT64                    uCodeLocationId;
    TEXT_POSITION             posBeg;
    TEXT_POSITION             posEnd;
    BSTR                      bstrDocumentUrl;
    DWORD                     dwByteOffset;
    DISASSEMBLY_FLAGS         dwFlags;
} DisassemblyData;
```

```csharp
public struct DisassemblyData { 
    public uint          dwFields;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrCodeBytes;
    public string        bstrOpcode;
    public string        bstrOperands;
    public string        bstrSymbol;
    public ulong         uCodeLocationId;
    public TEXT_POSITION posBeg;
    public TEXT_POSITION posEnd;
    public string        bstrDocumentUrl;
    public uint          dwByteOffset;
    public uint          dwFlags;
};
```

## <a name="members"></a>Members
`dwFields`\
Costante [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) che specifica quali campi vengono compilati.

`bstrAddress`\
Indirizzo come offset da un punto iniziale (in genere l'inizio della funzione associata).

`bstrCodeBytes`\
Byte di codice per questa istruzione.

`bstrOpcode`\
Codice operativo per questa istruzione.

`bstrOperands`\
Operandi per questa istruzione.

`bstrSymbol`\
Nome del simbolo, se presente, associato all'indirizzo (simbolo pubblico, etichetta e così via).

`uCodeLocationId`\
Identificatore della posizione del codice per questa riga disassemblata. Se l'indirizzo del contesto del codice di una riga è maggiore dell'indirizzo del contesto del codice di un'altra riga, anche l'identificatore della posizione del codice disassemblato della prima sarà maggiore dell'identificatore della posizione del codice della seconda.

`posBeg`\
Oggetto [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) corrispondente alla posizione in un documento in cui iniziano i dati disassembly.

`posEnd`\
Oggetto [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) corrispondente alla posizione in un documento in cui terminano i dati disassembly.

`bstrDocumentUrl`\
Per i documenti di testo che possono essere rappresentati come nomi di file, il campo viene compilato con il nome del file in cui è possibile trovare l'origine, `bstrDocumentUrl` usando il formato `file://file name` .

Per i documenti di testo che non possono essere rappresentati come nomi di file, è un identificatore univoco per il documento e il motore di debug deve `bstrDocumentUrl` implementare il [metodo GetDocument.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)

Questo campo può contenere anche informazioni aggiuntive sui checksum. Per ulteriori informazioni, vedere Note.

`dwByteOffset`\
Numero di byte dell'istruzione dall'inizio della riga di codice.

`dwFlags`\
Costante [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) che specifica quali flag sono attivi.

## <a name="remarks"></a>Commenti
Ogni `DisassemblyData` struttura descrive un'istruzione di disassembly. Una matrice di queste strutture viene restituita dal [metodo Read.](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)

La [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) viene usata solo per i documenti basati su testo. L'intervallo di codice sorgente per questa istruzione viene compilato solo per la prima istruzione generata da un'istruzione o da una riga, ad esempio quando `dwByteOffset == 0` .

Per i documenti non testuali, è possibile ottenere un contesto di documento dal codice e il `bstrDocumentUrl` campo deve essere un valore Null. Se il `bstrDocumentUrl` campo è uguale al campo `bstrDocumentUrl` nell'elemento della `DisassemblyData` matrice precedente, impostare su un valore `bstrDocumentUrl` Null.

Se per `dwFlags` il campo è impostato il flag , le informazioni aggiuntive sul `DF_DOCUMENT_CHECKSUM` checksum seguono la stringa a cui punta il `bstrDocumentUrl` campo. In particolare, dopo il carattere di terminazione della stringa Null, segue un GUID che identifica l'algoritmo di checksum seguito a sua volta da un valore a 4 byte che indica il numero di byte nel checksum e che a sua volta è seguito dai byte di checksum. Vedere l'esempio in questo argomento su come codificare e decodificare questo campo in [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] .

## <a name="example"></a>Esempio
Se il flag è impostato, il campo può contenere informazioni aggiuntive diverse `bstrDocumentUrl` `DF_DOCUMENT_CHECKSUM` da una stringa. Il processo di creazione e lettura di questa stringa codificata è semplice in [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] . Tuttavia, in [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] è un altro argomento. L'esempio seguente illustra un modo per creare la stringa codificata da e un modo per decodificare [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] la stringa codificata in [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] .

```csharp
using System;
using System.Runtime.InteropServices;

namespace MyNamespace
{
    class MyClass
    {
        string EncodeData(string documentString,
                          Guid checksumGuid,
                          byte[] checksumData)
        {
            string returnString = documentString;

            if (checksumGuid == null || checksumData == null)
            {
                // Nothing more to do. Just return the string.
                return returnString;
            }

            returnString += '\0'; // separating null value

            // Add checksum GUID to string.
            byte[] guidDataArray  = checksumGuid.ToByteArray();
            int    guidDataLength = guidDataArray.Length;
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);
            for (int i = 0; i < guidDataLength; i++)
            {
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);
            }
            // Copy guid data bytes to string as wide characters.
            // Assumption: sizeof(char) == 2.
            for (int i = 0; i < guidDataLength / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum count (a 32-bit value).
            Int32 checksumCount = checksumData.Length;
            Marshal.StructureToPtr(checksumCount, pBuffer, true);
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }

            // Add checksum data.
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);
            for (int i = 0; i < checksumCount; i++)
            {
                Marshal.WriteByte(pBuffer, i, checksumData[i]);
            }
            for (int i = 0; i < checksumCount / sizeof(char); i++)
            {
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));
            }
            Marshal.FreeCoTaskMem(pBuffer);

            return returnString;
        }

        void DecodeData(    string encodedString,
                        out string documentString,
                        out Guid   checksumGuid,
                        out byte[] checksumData)
        {
            documentString = String.Empty;
            checksumGuid = Guid.Empty;
            checksumData = null;

            IntPtr pBuffer = Marshal.StringToBSTR(encodedString);
            if (null != pBuffer)
            {
                int bufferOffset = 0;

                // Parse string out. String is assumed to be Unicode.
                documentString = Marshal.PtrToStringUni(pBuffer);
                bufferOffset += (documentString.Length + 1) * sizeof(char);

                // Parse Guid out.
                // Read guid bytes from buffer and store in temporary
                // buffer that contains only the guid bytes. Then the
                // Marshal.PtrToStructure() can work properly.
                byte[] guidDataArray  = checksumGuid.ToByteArray();
                int    guidDataLength = guidDataArray.Length;
                IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);
                for (int i = 0; i < guidDataLength; i++)
                {
                    Marshal.WriteByte(pGuidBuffer, i,
                                      Marshal.ReadByte(pBuffer, bufferOffset + i));
                }
                bufferOffset += guidDataLength;
                checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));
                Marshal.FreeCoTaskMem(pGuidBuffer);

                // Parse out the number of checksum data bytes (always 32-bit value).
                int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);
                bufferOffset += sizeof(Int32);

                // Parse out the checksum data.
                checksumData = new byte[dataCount];
                for (int i = 0; i < dataCount; i++)
                {
                    checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Vedi anche
- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
