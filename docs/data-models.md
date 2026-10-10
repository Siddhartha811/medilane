# Data models

- User: name, email (unique), passwordHash, role (doctor|admin), isActive, failedLoginCount, lockUntil, lastLoginAt
- RefreshToken: user, tokenHash, family, expiresAt, revokedAt, replacedBy, ip, userAgent
- Patient: fullName, mobile (encrypted), mobileHash (HMAC, for lookup), age, gender, language
- Consent: patient, version, language, purposes[], acceptedAt, ip, userAgent
- Interview: patient, language, status (in_progress|completed|abandoned), currentQuestionId,
  answers[{questionId, value, answeredAt}], extracted{symptoms, duration, severity, medications, allergies, history}, completedAt
- Document: patient, interview, cloudinaryId, mimeType, size, ocrText (encrypted), structured, status
- Summary: interview, text (encrypted), source (ai|fallback), model, generatedAt
- Visit: patient, interview, summary, redFlags[{code, label, severity, matchedText}], priority,
  status (waiting|in_review|reviewed), assignedDoctor, reviewedAt
- Prescription: visit, patient, doctor, medicines[{name, dose, frequency, duration, instructions}],
  advice, followUpDate, pdfPublicId, emailSentAt, status (draft|issued)
- AuditLog: actor{type, id, role}, action, resource{type, id}, ip, userAgent, metadata, createdAt
