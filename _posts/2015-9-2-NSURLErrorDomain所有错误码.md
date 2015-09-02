---
layout: post
title: NSURLErrorDomain所有错误码
---


###NSURLErrorDomain所有错误码
	/*!
	    @enum NSURL-related Error Codes
	    @abstract Constants used by NSError to indicate errors in the WebFoundation domain
	    @discussion Documentation on each constant forthcoming.
	*/
	enum
	{
	    NSURLErrorUnknown = 			-1,
	    NSURLErrorCancelled = 			kCFURLErrorCancelled,
	    NSURLErrorBadURL = 				kCFURLErrorBadURL,
	    NSURLErrorTimedOut = 			kCFURLErrorTimedOut,
	    NSURLErrorUnsupportedURL = 			kCFURLErrorUnsupportedURL,
	    NSURLErrorCannotFindHost = 			kCFURLErrorCannotFindHost,
	    NSURLErrorCannotConnectToHost = 		kCFURLErrorCannotConnectToHost,
	    NSURLErrorNetworkConnectionLost = 		kCFURLErrorNetworkConnectionLost,
	    NSURLErrorDNSLookupFailed = 		kCFURLErrorDNSLookupFailed,
	    NSURLErrorHTTPTooManyRedirects = 		kCFURLErrorHTTPTooManyRedirects,
	    NSURLErrorResourceUnavailable = 		kCFURLErrorResourceUnavailable,
	    NSURLErrorNotConnectedToInternet = 		kCFURLErrorNotConnectedToInternet,
	    NSURLErrorRedirectToNonExistentLocation = 	kCFURLErrorRedirectToNonExistentLocation,
	    NSURLErrorBadServerResponse = 		kCFURLErrorBadServerResponse,
	    NSURLErrorUserCancelledAuthentication = 	kCFURLErrorUserCancelledAuthentication,
	    NSURLErrorUserAuthenticationRequired = 	kCFURLErrorUserAuthenticationRequired,
	    NSURLErrorZeroByteResource = 		kCFURLErrorZeroByteResource,
	    NSURLErrorCannotDecodeRawData =             kCFURLErrorCannotDecodeRawData,
	    NSURLErrorCannotDecodeContentData =         kCFURLErrorCannotDecodeContentData,
	    NSURLErrorCannotParseResponse =             kCFURLErrorCannotParseResponse,
	    NSURLErrorFileDoesNotExist = 		kCFURLErrorFileDoesNotExist,
	    NSURLErrorFileIsDirectory = 		kCFURLErrorFileIsDirectory,
	    NSURLErrorNoPermissionsToReadFile = 	kCFURLErrorNoPermissionsToReadFile,
	    NSURLErrorDataLengthExceedsMaximum NS_ENUM_AVAILABLE(10_5, 2_0) =	kCFURLErrorDataLengthExceedsMaximum,
	    
	    // SSL errors
	    NSURLErrorSecureConnectionFailed = 		kCFURLErrorSecureConnectionFailed,
	    NSURLErrorServerCertificateHasBadDate = 	kCFURLErrorServerCertificateHasBadDate,
	    NSURLErrorServerCertificateUntrusted = 	kCFURLErrorServerCertificateUntrusted,
	    NSURLErrorServerCertificateHasUnknownRoot = kCFURLErrorServerCertificateHasUnknownRoot,
	    NSURLErrorServerCertificateNotYetValid = 	kCFURLErrorServerCertificateNotYetValid,
	    NSURLErrorClientCertificateRejected = 	kCFURLErrorClientCertificateRejected,
	    NSURLErrorClientCertificateRequired =	kCFURLErrorClientCertificateRequired,
	    NSURLErrorCannotLoadFromNetwork = 		kCFURLErrorCannotLoadFromNetwork,
	    
	    // Download and file I/O errors
	    NSURLErrorCannotCreateFile = 		kCFURLErrorCannotCreateFile,
	    NSURLErrorCannotOpenFile = 			kCFURLErrorCannotOpenFile,
	    NSURLErrorCannotCloseFile = 		kCFURLErrorCannotCloseFile,
	    NSURLErrorCannotWriteToFile = 		kCFURLErrorCannotWriteToFile,
	    NSURLErrorCannotRemoveFile = 		kCFURLErrorCannotRemoveFile,
	    NSURLErrorCannotMoveFile = 			kCFURLErrorCannotMoveFile,
	    NSURLErrorDownloadDecodingFailedMidStream = kCFURLErrorDownloadDecodingFailedMidStream,
	    NSURLErrorDownloadDecodingFailedToComplete =kCFURLErrorDownloadDecodingFailedToComplete,
	
	    NSURLErrorInternationalRoamingOff NS_ENUM_AVAILABLE(10_7, 3_0) =         kCFURLErrorInternationalRoamingOff,
	    NSURLErrorCallIsActive NS_ENUM_AVAILABLE(10_7, 3_0) =                    kCFURLErrorCallIsActive,
	    NSURLErrorDataNotAllowed NS_ENUM_AVAILABLE(10_7, 3_0) =                  kCFURLErrorDataNotAllowed,
	    NSURLErrorRequestBodyStreamExhausted NS_ENUM_AVAILABLE(10_7, 3_0) =      kCFURLErrorRequestBodyStreamExhausted,
	};

###CFNetworkErrors所有错误码
	/*
	 *  CFNetworkErrors
	 *  
	 *  Discussion:
	 *	The list of all public error codes returned under the error domain
	 *	kCFErrorDomainCFNetwork
	 */
	enum CFNetworkErrors {
	  kCFHostErrorHostNotFound = 1,
	  kCFHostErrorUnknown = 2, // Query the kCFGetAddrInfoFailureKey to get the value returned from getaddrinfo; lookup in netdb.h
	  // SOCKS errors; in all cases you may query kCFSOCKSStatusCodeKey to recover the status code returned by the server
	  kCFSOCKSErrorUnknownClientVersion = 100,
	  kCFSOCKSErrorUnsupportedServerVersion = 101, // Query the kCFSOCKSVersionKey to find the version requested by the server
	  // SOCKS4-specific errors
	  kCFSOCKS4ErrorRequestFailed = 110,  // request rejected or failed by the server
	  kCFSOCKS4ErrorIdentdFailed = 111,  // request rejected because SOCKS server cannot connect to identd on the client
	  kCFSOCKS4ErrorIdConflict = 112,  // request rejected because the client program and identd report different user-ids
	  kCFSOCKS4ErrorUnknownStatusCode = 113,
	  // SOCKS5-specific errors
	  kCFSOCKS5ErrorBadState = 120,
	  kCFSOCKS5ErrorBadResponseAddr = 121,
	  kCFSOCKS5ErrorBadCredentials = 122,
	  kCFSOCKS5ErrorUnsupportedNegotiationMethod = 123, // query kCFSOCKSNegotiationMethodKey to find the method requested
	  kCFSOCKS5ErrorNoAcceptableMethod = 124,
	  // FTP errors; query the kCFFTPStatusCodeKey to get the status code returned by the server
	  kCFFTPErrorUnexpectedStatusCode = 200,
	  // HTTP errors
	  kCFErrorHTTPAuthenticationTypeUnsupported = 300,
	  kCFErrorHTTPBadCredentials = 301,
	  kCFErrorHTTPConnectionLost = 302,
	  kCFErrorHTTPParseFailure = 303,
	  kCFErrorHTTPRedirectionLoopDetected = 304,
	  kCFErrorHTTPBadURL = 305,
	  kCFErrorHTTPProxyConnectionFailure = 306,
	  kCFErrorHTTPBadProxyCredentials = 307,
	  kCFErrorPACFileError = 308,
	  kCFErrorPACFileAuth = 309,
	  kCFErrorHTTPSProxyConnectionFailure = 310,
	  kCFStreamErrorHTTPSProxyFailureUnexpectedResponseToCONNECTMethod = 311,
		
	  // Error codes for CFURLConnection and CFURLProtocol
	  kCFURLErrorUnknown = -998,
	  kCFURLErrorCancelled = -999,
	  kCFURLErrorBadURL = -1000,
	  kCFURLErrorTimedOut = -1001,
	  kCFURLErrorUnsupportedURL = -1002,
	  kCFURLErrorCannotFindHost = -1003,
	  kCFURLErrorCannotConnectToHost = -1004,
	  kCFURLErrorNetworkConnectionLost = -1005,
	  kCFURLErrorDNSLookupFailed = -1006,
	  kCFURLErrorHTTPTooManyRedirects = -1007,
	  kCFURLErrorResourceUnavailable = -1008,
	  kCFURLErrorNotConnectedToInternet = -1009,
	  kCFURLErrorRedirectToNonExistentLocation = -1010,
	  kCFURLErrorBadServerResponse = -1011,
	  kCFURLErrorUserCancelledAuthentication = -1012,
	  kCFURLErrorUserAuthenticationRequired = -1013,
	  kCFURLErrorZeroByteResource = -1014,
	  kCFURLErrorCannotDecodeRawData = -1015,
	  kCFURLErrorCannotDecodeContentData = -1016,
	  kCFURLErrorCannotParseResponse = -1017,
	  kCFURLErrorInternationalRoamingOff = -1018,
	  kCFURLErrorCallIsActive = -1019,
	  kCFURLErrorDataNotAllowed = -1020,
	  kCFURLErrorRequestBodyStreamExhausted = -1021,
	  kCFURLErrorFileDoesNotExist = -1100,
	  kCFURLErrorFileIsDirectory = -1101,
	  kCFURLErrorNoPermissionsToReadFile = -1102,
	  kCFURLErrorDataLengthExceedsMaximum = -1103,
	  // SSL errors
	  kCFURLErrorSecureConnectionFailed = -1200,
	  kCFURLErrorServerCertificateHasBadDate = -1201,
	  kCFURLErrorServerCertificateUntrusted = -1202,
	  kCFURLErrorServerCertificateHasUnknownRoot = -1203,
	  kCFURLErrorServerCertificateNotYetValid = -1204,
	  kCFURLErrorClientCertificateRejected = -1205,
	  kCFURLErrorClientCertificateRequired = -1206,
	  kCFURLErrorCannotLoadFromNetwork = -2000,
	  // Download and file I/O errors
	  kCFURLErrorCannotCreateFile = -3000,
	  kCFURLErrorCannotOpenFile = -3001,
	  kCFURLErrorCannotCloseFile = -3002,
	  kCFURLErrorCannotWriteToFile = -3003,
	  kCFURLErrorCannotRemoveFile = -3004,
	  kCFURLErrorCannotMoveFile = -3005,
	  kCFURLErrorDownloadDecodingFailedMidStream = -3006,
	  kCFURLErrorDownloadDecodingFailedToComplete = -3007,
		
	  // Cookie errors
	  kCFHTTPCookieCannotParseCookieFile = -4000,
	
	  // Errors originating from CFNetServices
	  kCFNetServiceErrorUnknown = -72000L,
	  kCFNetServiceErrorCollision = -72001L,
	  kCFNetServiceErrorNotFound = -72002L,
	  kCFNetServiceErrorInProgress = -72003L,
	  kCFNetServiceErrorBadArgument = -72004L,
	  kCFNetServiceErrorCancel = -72005L,
	  kCFNetServiceErrorInvalid = -72006L,
	  kCFNetServiceErrorTimeout = -72007L,
	  kCFNetServiceErrorDNSServiceFailure = -73000L // An error from DNS discovery; look at kCFDNSServiceFailureKey to get the error number and interpret using dns_sd.h	
	};
	typedef enum CFNetworkErrors CFNetworkErrors;
		
