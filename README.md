# KBN-Dataset

**KBN-Dataset**은  Knowledge Base Population (KBP)모델을 통해 만든 데이터셋이며,  \
한국어 데이터셋 `KBN-KO v1.0`과 영어 데이터셋 `KBN-EN v1.0`으로 구성되어 있다. \
`KBN-KO v1.0`은 한국어-위키피디아 코퍼스에 대해 **Entity Recognition  + Relation Extraction** 기반 KBP을 사용하여 구축하였다. \
`KBN-EN v1.0`은 영어-위키피디아 코퍼스 대해 **OpenIE + Coreference** 기반 KBP를 사용하여 구축하였다.

## 목차
* [파일 형식](#파일-형식)
* [KBN-KO v1.0](#KBN_KO-v1.0)
* [KBN-EN v1.0](#KBN_EN-v1.0)


## 파일 형식
| 데이터명| 파일 수 | 문장 수 | 크기 |  포멧  | 
| :---: | :---: | :---: | :---: |  :---: |
| KBN-KO 1.0 | 410개 |  4,098,370 | 3.57GB  | json
| KBN-EN 1.0 | 8개 |  2,031,694 |  2.37GB  |json 


## KBN_KO v1.0
한국어-위키피디아 코퍼스에 대해 트리플 분석을 수행한 결과 데이터셋이다.  \
`file_name`, `sentence`은 KBP 수행전 원본 데이터 셋의 위치, 원본 문장을 나타낸다. \
`subject`, `subject_tag`, `subject_pos`은 문장내에서 주체에 해당하는 개체명과 태그, 위치를 나타내며  \
`object`, `object_tag`, `object_pos` 는 문장내에서 대상에 해당하는 개체명과 태그, 위치를 나타낸다.  \
`relation`, `description`, `confidence` 는 주체와 대상간의 관계태그와 관계태그에 대한 설명, 신뢰도를 나타낸다.

#### 관계태그
사전에 미리 정의되어 있다.(`/relation_info.txt` 참고)


#### 데이터 예시 
```py
{
    "file_name": "/wikipedia/entity/wikipedia_0001.json",
    "sentence": "제임스 얼 \"지미\"카터 주니어(, 1924년 10월 1일 ~ )는 민주당 출신 미국 39번째 대통령 (1977년 ~ 1981년)이다.",
    "subject": "제임스 얼",
    "subject_tag": "PS",
    "subject_pos": [0,5
    ],
    "object": "카터 주니어",
    "object_tag": "PS",
    "object_pos": [10,16
    ],
    "relation": "successor",
    "description": "항목 주제의 후임자",
    "confidence": 0.8254553079605103
},
```

## KBN_EN v1.0
영어-위키피디아 코퍼스에 대해 트리플 분석을 수행한 결과 데이터셋이다. \
`file_name`, `sentence`은 KBP 수행전 원본 데이터 셋의 위치, 원본 문장을 나타낸다. \
`subject`, `subject_start_pos`, `subject_corefernece`는 문장내에서 주체에 해당하는 개체명, 개체명의 위치, 상호참조되는 개체명들을 나타낸다.\
`object`, `object_start_pos`, `object_corefernece` 는 문장내에서 대상에 해당하는 개체명, 개체명의 위치, 상호참조되는 개체명들을 나타낸다.\
`relation`, `relation_start_pos`, `confidence` 는 주체와 대상간의 관계태그,  문장내의 관계태그의 위치, 신뢰도를 나타낸다.


#### 관계태그
문장내에서 추출되며 그 종류에 제한이 없다.

#### 데이터 예시 
```py
{
        "file_name": "AA_wiki_99_62",
        "sentence": "In philosophy, Leibniz is most noted for his optimism, i.e. his conclusion that our universe is, in a restricted sense, the best possible one that God could have created, an idea that was often lampooned by others such as Voltaire. Leibniz, along with René Descartes and Baruch Spinoza, was one of the three great 17th-century advocates of rationalism. The work of Leibniz anticipated modern logic and analytic philosophy, but his philosophy also assimilates elements of the scholastic tradition, notably that conclusions are produced by applying reason to first principles or prior definitions rather than to empirical evidence.",
        "confidence": "2.92848402261734",
        "average_confidence": 0.732121005654335,
        "relation": "noted",
        "subject": "Leibniz",
        "object": [
            "for his",
            "In"
        ],
        "relation_start_pos": "5",
        "subject_start_pos": "2",
        "object_start_pos": [
            "6",
            "0"
        ],
        "subject_corefernece": [
            "In",
            "but",
            "ime",
            "ib",
            "September",
            "Vol",
            ".",
            "s",
            "aph"
        ],
        "object_corefernece": [
            [
                "Von Neumann machine , which is",
                "is most noted for his op",
                "Newton ' s contempor",
                "often lampooned by others",
                "ism . The work of Le"
            ],
            [
                "In",
                "ti"
            ]
        ]
    },
```
