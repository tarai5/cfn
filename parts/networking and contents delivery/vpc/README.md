# VPC
ユーザーが指定した CIDR ブロックを持つ Virtual Private Cloud (VPC) を作成します

# プロパティ
[プロパティ](https://docs.aws.amazon.com/ja_jp/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-vpc.html#w2ab2c21c10d469b9)

# 戻り値
作成されたVPCの論理ID

# 例
~~~~
{
  "Mappings" : {
    "CloudFormationSettings" : {
      "S3" : {
        "TemplateDir" : "https://s3.us-east-2.amazonaws.com/cf-templates-j648jx7tgtus-us-east-2/"  
      }  
    }  
  },  
  "Resources": {  
    "VPCStack": {  
      "Type": "AWS::CloudFormation::Stack",  
      "Properties": {  
        "TemplateURL"     : { "Fn::Join": ["", [{ "Fn::FindInMap": [ "CloudFormationSettings", "S3", "TemplateDir"]},"vpc.json"]]}   
      }  
    }  
  }  
}  
~~~~
 