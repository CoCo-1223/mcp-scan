# MCP-Scan 보안 강화 프로젝트 🔒

Model Context Protocol (MCP) 스캐닝 도구의 보안성을 강화하는 종합적인 보안 개선 프로젝트입니다. 입력 검증, Circuit Breaker 패턴, 견고한 보안 모니터링에 중점을 두고 있습니다.

## Goal

이 프로젝트는 **MCP-Scan의 사용성과 안정성을 크게 개선**하여 개발자와 보안 담당자들이 더 쉽고 효율적으로 MCP 서버의 보안을 관리할 수 있도록 하는 것을 목표로 합니다. 

### 🎯 **핵심 개선 목표**

**1. 🛡️ 사용자 친화적 오류 처리**
- MCP 설정 파일의 JSON 형식 오류나 필수 필드 누락 시 명확하고 이해하기 쉬운 오류 메시지 제공
- 기존의 복잡한 기술적 에러를 일반 사용자도 쉽게 이해할 수 있는 안내 메시지로 개선
- 설정 파일 경로 문제 등 일반적인 실수에 대한 즉각적인 해결 방법 제시

**2. ⚡ 시각적 피드백 강화**
- Rich 라이브러리를 활용한 컬러풀하고 직관적인 로그 출력 시스템
- 실시간 진행률 표시로 사용자가 스캔 진행 상황을 명확히 파악할 수 있도록 개선
- 로그 레벨별 색상 구분으로 중요한 정보와 일반 정보를 쉽게 구별

**3. 💾 성능 최적화**
- 파일 해시 기반 지능형 캐싱 시스템으로 동일한 설정 파일 재스캔 시 즉시 결과 제공
- 불필요한 중복 작업 제거로 전체 스캔 시간 50% 이상 단축
- 캐시 상태 표시로 사용자가 캐시 활용 현황을 쉽게 확인

**4. 🔧 CLI 사용성 대폭 개선**
- 초보자도 쉽게 따라할 수 있는 상세한 도움말과 실제 사용 예시 제공
- 일반적인 오류 상황별 해결 방법을 포함한 스마트 에러 가이드
- 명령어 옵션의 직관적인 그룹화 및 설명으로 학습 곡선 완화

**5. 📊 포괄적 리포트 시스템**
- 스캔 결과를 한눈에 파악할 수 있는 아름다운 HTML 리포트 자동 생성
- 위험도별 분류와 개선 권장사항을 포함한 실행 가능한 보안 가이드 제공
- 경영진이나 팀장에게 보고하기 적합한 전문적인 요약 문서 생성

### 🌟 **프로젝트의 차별점**

기존의 복잡하고 기술적인 보안 도구와 달리, **일반 개발자도 쉽게 사용할 수 있는 친근한 도구**로 발전시키는 것이 이 프로젝트의 핵심입니다. 단순히 기능을 추가하는 것이 아니라, 사용자 경험(UX)을 중심으로 한 종합적인 개선을 통해 MCP 보안 관리의 접근성을 높입니다.

### 👥 **대상 사용자**

- **주니어 개발자**: 복잡한 보안 설정 없이도 쉽게 MCP 보안 상태를 확인하고 싶은 개발자
- **팀 리더**: 팀의 MCP 서버 보안 현황을 주기적으로 모니터링하고 리포트를 작성해야 하는 리더
- **DevOps 엔지니어**: CI/CD 파이프라인에 보안 검사를 자동화하고 싶은 엔지니어
- **프리랜서/1인 개발자**: 복잡한 보안 도구 없이도 기본적인 보안 점검을 수행하고 싶은 개발자

### 🎯 **성공 지표**

이 프로젝트가 성공했다고 판단할 수 있는 기준:
- 설정 오류 시 해결 시간이 기존 대비 70% 단축
- 스캔 결과를 이해하고 조치하는 데 필요한 시간 50% 감소  
- 반복 스캔 성능 50% 이상 향상
- 비전문가도 5분 안에 기본 스캔을 수행하고 결과를 이해할 수 있음

## Requirements

### 시스템 요구사항
- **Python**: >= 3.10.0
- **Docker**: >= 20.10.0
- **메모리**: 최소 2GB RAM, 권장 4GB+
- **저장공간**: 캐싱 및 로그용 1GB 여유 공간

### 핵심 의존성
```
mcp[cli] >= 1.6.0          # Model Context Protocol CLI 도구
requests >= 2.32.3         # API 호출용 HTTP 라이브러리
rich >= 14.0.0            # 리치 텍스트 및 아름다운 포맷팅
pyjson5 >= 1.6.8          # 설정 파일용 JSON5 파서
pydantic >= 2.11.2        # 데이터 검증 및 설정 관리
lark-parser[regex] >= 0.12.0  # 보안 규칙용 문법 파싱
```

### 개발 의존성
```
pytest >= 7.0.0           # 테스팅 프레임워크
pytest-asyncio >= 0.21.0  # 비동기 테스팅 지원
pytest-cov >= 4.0.0       # 커버리지 리포팅
black >= 23.0.0           # 코드 포맷팅
flake8 >= 6.0.0           # 린팅 및 스타일 검사
bandit >= 1.7.5           # 보안 취약점 스캐너
safety >= 2.3.0           # 의존성 취약점 검사기
```

### 보안 강화 라이브러리
```
cryptography >= 41.0.0    # 보안 검증용 암호화 연산
psutil >= 5.9.0          # 리소스 관리용 시스템 모니터링
aiofiles >= 23.1.0       # 비동기 파일 연산
aiosqlite >= 0.19.0      # 캐싱용 비동기 SQLite
```

## How to install & Run

### 사전 요구사항
시스템에 Docker가 설치되어 실행 중인지 확인하세요:
```bash
docker --version  # Docker 버전 20.10.0+ 표시되어야 함
```

### 1단계: Docker 이미지 다운로드 및 설치

#### 방법 A: Docker Hub에서 다운로드 (권장)
```bash
# 최신 안정 버전 이미지 다운로드
docker pull coco1223/mcp-scan-security:latest

# 이미지 확인
docker images | grep mcp-scan-security
```

#### 방법 B: 소스코드에서 빌드
```bash
# 저장소 클론
git clone https://github.com/CoCo-1223/mcp-scan.git
cd mcp-scan

# Docker 이미지 빌드
docker build -t coco1223/mcp-scan-security:latest -f Dockerfile .

# 빌드 확인
docker images | grep mcp-scan-security
```

### 2단계: Docker 컨테이너 생성 및 실행

#### 기본 컨테이너 설정
```bash
# 보안 강화가 포함된 컨테이너 생성 및 실행
docker run -it --name mcp-scan-security \
  -v $(pwd)/data:/app/data \
  -v $(pwd)/config:/app/config \
  -v $(pwd)/logs:/app/logs \
  -p 8080:8080 \
  --security-opt=no-new-privileges \
  --read-only \
  --tmpfs /tmp \
  coco1223/mcp-scan-security:latest
```

#### 고급 컨테이너 설정 (프로덕션용)
```bash
# 전용 네트워크 생성
docker network create mcp-scan-network

# 강화된 보안 및 모니터링으로 실행
docker run -d --name mcp-scan-security \
  --network mcp-scan-network \
  -v mcp-scan-data:/app/data \
  -v mcp-scan-config:/app/config \
  -v mcp-scan-logs:/app/logs \
  -p 8080:8080 \
  --restart unless-stopped \
  --memory=4g \
  --cpus=2 \
  --security-opt=no-new-privileges \
  --read-only \
  --tmpfs /tmp:rw,size=1g \
  -e SECURITY_MODE=enhanced \
  -e LOG_LEVEL=INFO \
  coco1223/mcp-scan-security:latest
```

#### 개발용 컨테이너 설정
```bash
# 개발 모드로 실행 (코드 변경사항 실시간 반영)
docker run -it --name mcp-scan-dev \
  -v $(pwd):/app \
  -v mcp-scan-cache:/app/cache \
  -p 8080:8080 \
  -p 9229:9229 \
  -e DEVELOPMENT=true \
  -e DEBUG=true \
  coco1223/mcp-scan-security:latest bash
```

### 3단계: 디렉토리 구조

프로젝트는 다음과 같은 체계적인 디렉토리 구조를 사용합니다:

```
mcp-scan/
├── src/                    # 소스코드 디렉토리
│   └── mcp_scan/
│       ├── cli.py         # CLI 인터페이스
│       ├── MCPScanner.py  # 메인 스캐너 클래스
│       ├── models.py      # 데이터 모델
│       ├── utils.py       # 유틸리티 함수
│       └── security/      # 보안 강화 모듈
│           ├── validator.py      # 입력 검증
│           ├── circuit_breaker.py # Circuit Breaker
│           ├── cache.py          # 캐싱 시스템
│           └── audit_logger.py   # 감사 로깅
├── tests/                  # 테스트 파일
│   ├── test_security.py   # 보안 기능 테스트
│   ├── test_scanner.py    # 스캐너 테스트
│   └── fixtures/          # 테스트 데이터
├── config/                 # 설정 파일
│   ├── security.yml       # 보안 설정
│   ├── cache.yml          # 캐시 설정
│   └── logging.yml        # 로깅 설정
├── data/                   # 데이터 디렉토리
│   ├── scans/             # 스캔 결과
│   ├── cache/             # 캐시 파일
│   └── whitelists/        # 화이트리스트
├── logs/                   # 로그 파일
│   ├── security.log       # 보안 이벤트 로그
│   ├── application.log    # 일반 애플리케이션 로그
│   └── audit/             # 감사 로그
├── docs/                   # 문서
│   ├── security.md        # 보안 가이드
│   └── api.md             # API 문서
├── scripts/                # 유틸리티 스크립트
│   ├── setup.sh           # 초기 설정
│   └── backup.sh          # 백업 스크립트
├── Dockerfile             # Docker 빌드 파일
├── docker-compose.yml     # 다중 컨테이너 설정
├── pyproject.toml         # Python 프로젝트 설정
├── requirements-dev.txt   # 개발 의존성
└── README.md              # 프로젝트 문서
```

**각 디렉토리의 용도**:
- `src/`: 모든 소스코드를 포함하며, 모듈별로 체계적으로 구성
- `tests/`: 단위 테스트, 통합 테스트, 보안 테스트를 포함
- `config/`: 환경별 설정 파일들을 YAML 형식으로 관리
- `data/`: 스캔 결과, 캐시, 화이트리스트 등 애플리케이션 데이터
- `logs/`: 구조화된 로그 파일들 (보안, 감사, 일반)

### 4단계: 애플리케이션 실행

#### 컨테이너 내에서 기본 스캔 실행
```bash
# 컨테이너에 접속
docker exec -it mcp-scan-security bash

# 기본 MCP 스캔 실행
mcp-scan scan --security-enhanced

# 특정 설정 파일 스캔
mcp-scan scan /app/config/claude.json --verbose

# 로컬 전용 모드로 스캔 (외부 API 사용 안함)
mcp-scan scan --local-only --output-format json
```

#### 보안 강화 기능 테스트
```bash
# 입력 검증 테스트
python -m pytest tests/test_security.py::test_input_validation -v

# Circuit Breaker 테스트
python -m pytest tests/test_security.py::test_circuit_breaker -v

# 전체 보안 테스트 실행
python -m pytest tests/test_security.py -v --cov=src/mcp_scan/security
```

#### 실시간 모니터링 및 로그 확인
```bash
# 보안 로그 실시간 모니터링
tail -f /app/logs/security.log

# 감사 로그 확인
cat /app/logs/audit/$(date +%Y-%m-%d).json | jq '.'

# 시스템 상태 확인
curl http://localhost:8080/health
```

### 5단계: 실행 종료 방법

#### 정상 종료 (Graceful Shutdown)
```bash
# 컨테이너 내에서 애플리케이션 종료
# Ctrl+C 또는 SIGTERM 시그널 전송
kill -TERM $(pgrep -f mcp-scan)

# 컨테이너 정상 종료
docker stop mcp-scan-security

# 종료 상태 확인
docker ps -a | grep mcp-scan-security
```

#### 강제 종료 및 정리
```bash
# 컨테이너 강제 종료
docker kill mcp-scan-security

# 컨테이너 제거
docker rm mcp-scan-security

# 이미지 제거 (필요시)
docker rmi coco1223/mcp-scan-security:latest

# 볼륨 정리 (주의: 데이터 손실)
docker volume rm mcp-scan-data mcp-scan-config mcp-scan-logs
```

#### 완전 정리 (개발 환경)
```bash
# 모든 관련 리소스 정리
docker-compose down -v --remove-orphans

# 네트워크 제거
docker network rm mcp-scan-network

# 빌드 캐시 정리
docker builder prune -f
```

#### 데이터 백업 후 종료
```bash
# 중요 데이터 백업
docker exec mcp-scan-security /app/scripts/backup.sh

# 백업 파일을 호스트로 복사
docker cp mcp-scan-security:/app/backup/$(date +%Y%m%d).tar.gz ./

# 안전하게 종료
docker stop mcp-scan-security
```

## 실행 성공 확인 방법

### 헬스 체크
```bash
# 애플리케이션 상태 확인
curl -f http://localhost:8080/health || echo "서비스 실행 중이 아님"

# 보안 기능 상태 확인
curl http://localhost:8080/security/status
```

### 로그 확인
```bash
# 최근 보안 이벤트 확인
docker exec mcp-scan-security tail -20 /app/logs/security.log

# 에러 로그 확인
docker logs mcp-scan-security --tail=50 | grep ERROR
```