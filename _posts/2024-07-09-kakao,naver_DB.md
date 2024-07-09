---

layout: single

title: "프로젝트)카카오, 네이버 로그인시 db저장"

categories: coding

tag: [blog, 백준]

toc: true

---

# 카카오 네이버 DB입력 작성

## 카카오, 네이버 db저장

기존 코드에서 로그인 성공시 db에 넣는 기능 구현을 성공했지만

로그인 할시에 계속 db에 저장 할려고해서 오류가나 2번째 로그인 부터는 오류로 인해서 로그인이 안됬다

이후 if문으로 해당 아이디가 있으면 바로 로그인이되고

아이디가 없으면 db에 값들을 저장후 로그인이 되게 설정 하였다,

```java
String kakaoId = "kakao_" + Long.toString((Integer) userInfo.get("id"));
		UserEntity existingUser = userRepository.findByUId(kakaoId);
        
        if (existingUser == null) {
            // 새로운 사용자 정보 설정
            UserEntity newUser = new UserEntity();
            newUser.setUMail((String) userInfo.get("email"));
            newUser.setUName((String) userInfo.get("nickname"));
            newUser.setURegister(LocalDate.now());
            newUser.setUPw(""); // 카카오 로그인에서는 비밀번호를 사용하지 않으므로 빈 값으로 설정
            newUser.setUPofile((String) userInfo.get("profile"));
            newUser.setUBirth(""); // 생일 정보는 카카오에서 따로 제공하지 않으므로 비워둠
            newUser.setUTel(""); // 전화번호 정보도 카카오에서 따로 제공하지 않으므로 비워둠
            newUser.setUId(kakaoId);
            
            userRepository.save(newUser); // 새로운 사용자 저장
            session.setAttribute("access_Token", access_Token);
            session.setAttribute("UId", newUser.getUId()); // 세션에 새로운 사용자 ID 설정
        }else {
        	session.setAttribute("access_Token", access_Token);
        	session.setAttribute("UId", existingUser.getUId());
        }
```



```java
UserEntity existingUser = userrepository.findByUId(naverId);
		System.out.println("아이디 확인 : " + existingUser);
		
		if(existingUser != null) {
			session.setAttribute("UId", naverId);
			System.out.println("네이버 세션 등록 : " + naverId);
			return "redirect:/";
		}else {
			UserEntity newUser = new UserEntity();
            newUser.setUMail(email);
            newUser.setUName("naver-" + naverProfileResponse.getResponse().getNickname());
            newUser.setURegister(LocalDate.now());
            newUser.setUPw(""); // 비밀번호는 네이버 로그인에서는 사용되지 않으므로 빈 값
            newUser.setUPofile(naverProfileResponse.getResponse().getProfile_image());
            newUser.setUBirth(naverProfileResponse.getResponse().getBirthyear() + "-" + naverProfileResponse.getResponse().getBirthday());
            newUser.setUTel(naverProfileResponse.getResponse().getMobile());
            newUser.setUId(naverProfileResponse.getResponse().getId());
            userrepository.save(newUser);

            session.setAttribute("UId", newUser.getUId());
            return "redirect:/";
		}
```

