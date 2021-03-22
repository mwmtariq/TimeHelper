# TimeHelper
Time Format Swift  ❤️


//
//  TimeHelper.swift
//
//  Created by Tariq Al-aqrabawi on 09/03/2021.
//  Copyright © 2021 iOS Team. All rights reserved.
//

import Foundation

class TimeHelper: NSObject {
    
    static func getCurrentDateTime(format:DateFormater = .Tuesday_Mar_9_2021, language:LocaleLanguage = .en, customFormat:String = "") -> String{
        
        let formatter = DateFormatter()
        formatter.locale = Locale(identifier: customFormat.isEmpty ? language.getTitleFor() : customFormat)
        formatter.dateFormat = format.getTitleFor()
        formatter.amSymbol = language.amSymble
        formatter.pmSymbol = language.pmSymble
        
        return formatter.string(from: Date())
    }
    
    enum DateFormater: String {
        
       // MARK: Tuesday, Mar 9, 2021
        case Tuesday_Mar_9_2021 = "EEEE, MMM d, yyyy"
        
        //MARK: 03/09/2021
        case Type_03_09_2021 = "MM/dd/yyyy"
        
        //MARK: 03-09-2021 13:50
        case Type_03_09_2021_13_50 = "MM-dd-yyyy HH:mm"
        
        //MARK: Mar 9, 1:50 PM
        case Mar_9_1_50_PM = "MMM d, h:mm a"
        
        //MARK: March 2021
        case March_2021 = "MMMM yyyy"
        
        //MARK: Mar 9, 2021
        case Mar_9_2021 = "MMM d, yyyy"
        
        //MARK: Tue, 9 Mar 2021 13:50:44 +0000
        case Tue_9_Mar_2021_13_50_44 = "E, d MMM yyyy HH:mm:ss"
        
        //MARK: 09.03.21
        case Type_09_03_21 = "dd.MM.yy"
        
        //MARK: 13:50:44
        case Type_13_50_44 = "HH:mm:ss"
        
        //MARK: 11:50 am
        case Type_11_50_am = "h:mm a"

        //MARK: 09/03/2021
        case Type2_09_03_2021 = "dd/MM/yyyy"

        func getTitleFor() -> String {
            return self.rawValue
        }
    }
    
    enum LocaleLanguage:String {
        case en = "en_US"
        case ar = "ar"
        
        func getTitleFor() -> String {
            return self.rawValue
        }
        
        var amSymble:String{
            switch self {
            case .ar:
                return "ص"
            case .en:
            return "AM"
            }
        }
        
        var pmSymble:String{
            switch self {
            case .ar:
                return "م"
            case .en:
            return "PM"
            }
        }
    }
    
}

