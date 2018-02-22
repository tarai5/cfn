# VPC
既存の VPC 内にサブネットを作成します。

# プロパティ
[プロパティ](https://docs.aws.amazon.com/ja_jp/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-subnet.html#aws-resource-ec2-subnet-properties)

# 戻り値
作成されたサブネットの論理ID

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


    "vpc001stack": {
      "Type": "AWS::CloudFormation::Stack",
      "Properties": { 
        "TemplateURL"     : { "Fn::Join": ["", [{ "Fn::FindInMap": [ "CloudFormationSettings", "S3", "TemplateDir"]},"vpc001.json"]]},
      "TimeoutInMinutes": "5"
      }
    },


    "subnet001stack": {
      "Type": "AWS::CloudFormation::Stack",
      "Properties": {
        "TemplateURL"     : { "Fn::Join": ["", [{ "Fn::FindInMap": [ "CloudFormationSettings", "S3", "TemplateDir"]},"subnet001.json"]]},
        "TimeoutInMinutes": "5",
	"Parameters"      : {
          "vpc001": { "Fn::GetAtt" : [ "vpc001stack", "Outputs.vpc001" ] }
        }
      }
    }


  }
}~~~~
 
