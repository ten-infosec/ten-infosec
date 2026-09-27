
# PQC 커리큘럼 로드맵 (Stage 1\~9)

정수론에서 시작해 양자내성암호(PQC), 양자키분배(QKD), 하드웨어 보안까지 이어지는 전체 학습 계획.
진로 방향: 정보보안 → 양자내성암호 → 우주 사이버보안

각 Stage에서 만든 결과물은 별도 저장소에 있고, 이 문서는 그 전체를 잇는 **지도** 역할을 한다.

## 한눈에 보기

| 구간 | Stage | 주제 | 저장소 · 기록 | 상태 |
|---|---|---|---|---|
| 기초 | 1 | 정수론 | [rsa-from-scratch](https://github.com/ten-infosec/rsa-from-scratch) | ✅ |
| 기초 | 2 | 전산학 기초 | Wireshark 실습 완료, 이론은 [linux-study](https://github.com/ten-infosec/linux-study) Part 2와 병행 | 🔄 |
| 기초 | 3 | C/C++ · 리눅스 | [linux-study](https://github.com/ten-infosec/linux-study) Part 0, 2 | ⬜ |
| 기초 | 4 | 네트워크 보안 · 암호학 기초 | [TLS·ML-KEM Wireshark 관찰 기록](https://github.com/ten-infosec/rsa-from-scratch/blob/main/notes/2026-09-26_tls-pqc-wireshark.md) | ⬜ |
| 진입 | 5 | PKI 실전 | linux-study Part 3-4 | ⬜ |
| 진입 | 6 | PQC | linux-study Part 3-4, 종합 프로젝트 | ⬜ |
| 확장 | 7 | QKD · QRNG | [qiskit-study](https://github.com/ten-infosec/qiskit-study) (양자 로드맵 Q1\~Q6) | 🔄 |
| 확장 | 8 | Secure Enclave · TEE | linux-study Part 4, 7 | ⬜ |
| 확장 | 9 | 암호화 가속 · Root of Trust · SoC | linux-study Part 7 | ⬜ |

상태 표시: ⬜ 시작 전 / 🔄 진행 중 / ✅ 완료

---

## 기초 구간

### Stage 1. 정수론 ✅

- 소수와 소인수분해
- 유클리드 호제법
- 모듈러 연산
- 모듈러 역원
- 페르마의 소정리 · 오일러 정리
- 실습: 작은 RSA 구현

→ 결과물: [rsa-from-scratch](https://github.com/ten-infosec/rsa-from-scratch) (구현 → 공격 → 증명 → 공격 시간 실험)

### Stage 2. 전산학 기초 🔄

- 자료구조 (배열, 연결리스트, 트리, 해시테이블)
- 프로세스 · 스레드
- 가상 메모리 · 페이징
- OSI 7계층 vs TCP/IP 4계층
- TCP 3-way 핸드셰이크
- 실습: Wireshark 핸드셰이크 캡처 · 계층 구조 확인

→ 이론 보강: [linux-study](https://github.com/ten-infosec/linux-study) Part 2-3 가상 메모리, 2-5 스케줄링, 2-7 네트워크 스택

### Stage 3. C/C++ · 리눅스

- 리눅스 환경, gcc · gdb
- 포인터와 메모리 주소
- malloc/free
- 컴파일 4단계
- 스택 vs 힙
- 버퍼 오버플로우 · use-after-free
- 실습: 버퍼 오버플로우 발생 · gdb 디버깅

→ 연결: [linux-study](https://github.com/ten-infosec/linux-study) Part 0 환경, 2-2 GDB, 2-4 Stack/Heap·버퍼 오버플로우

### Stage 4. 네트워크 보안 · 암호학 기초

- 대칭키(AES) vs 공개키(RSA)
- 해시함수 (SHA-256, 눈사태 효과)
- HMAC
- 디지털 서명
- TLS 핸드셰이크
- IPsec (전송 모드 vs 터널 모드)
- 실습: TLS 핸드셰이크 캡처 · 해시 눈사태 실험

→ 미리 해본 것: [브라우저 TLS에서 X25519MLKEM768 하이브리드 키 교환 관찰](https://github.com/ten-infosec/rsa-from-scratch/blob/main/notes/2026-09-26_tls-pqc-wireshark.md)
→ 연결: linux-study Part 3-4 OpenSSL, 1-7 tcpdump

## 진입 구간

### Stage 5. PKI 실전

- X.509 인증서 구조
- CA와 인증서 체인
- CRL · OCSP
- HSM
- 실습: OpenSSL로 루트 CA · 서버 인증서 발급 · nginx 적용

→ 연결: linux-study Part 3-4 자체 CA, Nginx HTTPS

### Stage 6. PQC

- 격자 기반 암호
- ML-KEM
- ML-DSA · SLH-DSA
- 하이브리드 방식
- 크립토 애자일리티
- 실습: liboqs 빌드 · OpenSSL 연동 · ML-KEM TLS 서버

→ 연결: linux-study Part 3-4 PQC TLS 서버, 종합 프로젝트 7번
→ 배경: qiskit-study Q4 (쇼어 알고리즘이 RSA를 깨는 원리 → PQC가 필요한 이유)

## 확장 구간

### Stage 7. QKD · QRNG 🔄

- 측정-교란 원리, no-cloning
- BB84 프로토콜
- FPGA · HDL
- 실습: BB84 손 시뮬레이션

→ 진행 중: [qiskit-study](https://github.com/ten-infosec/qiskit-study) — Qiskit으로 BB84 시뮬레이션, 양자 로드맵 Q1\~Q6로 선수 지식(선형대수, 양자역학 가설) 보강

### Stage 8. Secure Enclave · TEE

- Intel SGX · ARM TrustZone · AMD SEV
- 격리 vs 증명
- 실습: SGX Hello Enclave

→ 연결: linux-study Part 4-1 namespace·cgroup, Part 7-2 TrustZone

### Stage 9. 암호화 가속 · Root of Trust · SoC

- CUDA 기초
- Root of Trust · Secure Boot
- Attestation (DICE, SPDM, TPM)
- SoC 구조
- 실습: AES를 GPU로 병렬 처리 · CPU와 속도 비교

→ 연결: linux-study Part 7-2 NEON·암호 명령어, 7-3 Secure Boot
